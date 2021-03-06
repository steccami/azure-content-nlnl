<properties
   pageTitle="Uw ontwikkelomgeving instellen in Mac OS X | Microsoft Azure"
   description="Installeer de runtime, SDK en hulpprogramma's en maak een lokaal ontwikkelcluster. Zodra u dit hebt gedaan, kunt u toepassingen bouwen in Mac OS X."
   services="service-fabric"
   documentationCenter=".net"
   authors="seanmck"
   manager="timlt"
   editor=""/>

<tags
   ms.service="service-fabric"
   ms.devlang="dotNet"
   ms.topic="get-started-article"
   ms.tgt_pltfrm="NA"
   ms.workload="NA"
   ms.date="09/25/2016"
   ms.author="seanmck"/>


# Uw ontwikkelomgeving instellen in Mac OS X

> [AZURE.SELECTOR]
-[ Windows](service-fabric-get-started.md)
- [Linux](service-fabric-get-started-linux.md)
- [OSX](service-fabric-get-started-mac.md)

U kunt Service Fabric-toepassingen bouwen voor uitvoering op Linux-clusters met behulp van Mac OS X. In dit artikel wordt uitgelegd hoe u uw Mac kunt instellen voor ontwikkeling.

## Vereisten

Service Fabric wordt niet systeemeigen op OS X uitgevoerd. Als u een lokaal Service Fabric-cluster wilt uitvoeren, bieden we een vooraf geconfigureerde virtuele Ubuntu-machine met Vagrant en VirtualBox. Voordat u aan de slag gaat, hebt u het volgende nodig:

- [Vagrant (v1.8.4 of hoger)](http://wwww.vagrantup.com/downloads)
- [VirtualBox](http://www.virtualbox.org/wiki/Downloads)

## De lokale virtuele machine maken

Ga als volgt te werk om de lokale virtuele machine te maken met een Service Fabric-cluster met 5-knooppunten:

1. Kloon de Vagrantfile-opslagplaats

    ```bash
    git clone https://github.com/azure/service-fabric-linux-vagrant-onebox.git
    ```

2. Navigeer naar de lokale kloon van de opslagplaats

    ```bash
    cd service-fabric-linux-vagrant-onebox
    ```

3. Wijzig de standaardinstellingen van de virtuele machine (optioneel)

    Standaard wordt de lokale virtuele machine als volgt geconfigureerd:

    - 3 GB toegewezen geheugen
    - Persoonlijk hostnetwerk geconfigureerd op IP 192.168.50.50 dat passthrough van verkeer van de Mac-host inschakelt

    U kunt een van deze instellingen wijzigen of een andere configuratie toevoegen aan de virtuele machine in de Vagrantfile. Zie de [Vagrant-documentatie](http://www.vagrantup.com/docs) voor de volledige lijst met configuratieopties.

4. De virtuele machine maken

    ```bash
    vagrant up
    ```

    In deze stap wordt de vooraf geconfigureerde VM-installatiekopie gedownload, lokaal opgestart en wordt er vervolgens een lokaal Service Fabric-cluster in ingesteld. Dit kan enkele minuten duren. Als de installatie is voltooid, ziet u een bericht in de uitvoer dat aangeeft dat het cluster wordt gestart.

    ![Starten van clusterinstallatie na inrichting van VM][cluster-setup-script]

5. Test of het cluster correct is ingesteld door naar Service Fabric Explorer te gaan op http://192.168.50.50:19080/Explorer (ervan uitgaande dat u het standaard IP-adres van het privénetwerk hebt gehouden).

    ![Service Fabric Explorer bekeken vanuit de host-Mac][sfx-mac]


## De Service Fabric-invoegtoepassing installeren voor Eclipse Neon (optioneel)

Service Fabric biedt een invoegtoepassing voor de Eclipse Neon IDE die het proces van het maken en implementeren van Java-services kan vereenvoudigen.

1. Zorg ervoor dat u in Eclips Buildship versie 1.0.17 of hoger hebt geïnstalleerd. U kunt de versies van geïnstalleerde onderdelen controleren door **Help > Installation Details** te kiezen. U kunt Buildship bijwerken met behulp van [deze instructies][buildship-bijwerken].

2. Als u de Service Fabric-invoegtoepassing wilt installeren, kiest u **Help > Install New Software...**

3. Voer in het tekstvak 'Work with' het volgende in: http://dl.windowsazure.com/eclipse/servicefabric.

4. Klik op Add.

    ![Eclipse Neon-invoegtoepassing voor Service Fabric][sf-eclipse-plugin-install]

5. Kies de Service Fabric-invoegtoepassing en klik op Next.

6. Doorloop de installatie en accepteer de gebruiksrechtovereenkomst.

## Volgende stappen

- [Uw eerste Service Fabric-toepassing voor Linux maken](service-fabric-create-your-first-linux-application-with-java.md)

<!-- Links -->

- [Een Service Fabric-cluster maken in Azure Portal](service-fabric-cluster-creation-via-portal.md)
- [Een Service Fabric-cluster maken met behulp van de Azure Resource Manager](service-fabric-cluster-creation-via-arm.md)
- [Inzicht krijgen in het Service Fabric-toepassingsmodel](service-fabric-application-model.md)

<!-- Images -->
[cluster-installatie-script]: ./media/service-fabric-get-started-mac/cluster-setup-mac.png
[sfx-mac]: ./media/service-fabric-get-started-mac/sfx-mac.png
[sf-eclipse-invoegtoepassing-installeren]: ./media/service-fabric-get-started-mac/sf-eclipse-plugin-install.png
[buildship-bijwerken]: https://projects.eclipse.org/projects/tools.buildship



<!--HONumber=Sep16_HO4-->


