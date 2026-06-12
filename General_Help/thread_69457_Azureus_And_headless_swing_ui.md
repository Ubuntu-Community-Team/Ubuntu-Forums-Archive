---
title: "Azureus And headless swing ui"
date: 2005-09-26
forum: General Help
---

### Post by ubuntme on 2005-09-26
I am trying to set up a headless ubuntu box so that I can download torrents remotly using Azureuzs.

I have been following this guide [http://azureus.aelitis.com/wiki/index.php/ConsoleUI]("http://azureus.aelitis.com/wiki/index.php/ConsoleUI")

I have istalled all the appropriate .jar files in .Azureus/ And every thing starts ok.

However, there are a couple of problems.
Firstly, I can seem to connect to a torrent from the console UI, I get this error:
```
java.io.IOException: Connection attempt aborted: timed out after 30sec
        at com.aelitis.azureus.core.versioncheck.VersionCheckClient.performVersionCheck(Unknown Source)
        at com.aelitis.azureus.core.versioncheck.VersionCheckClient.getVersionCheckInfo(Unknown Source)
        at com.aelitis.azureus.core.versioncheck.VersionCheckClient.getExternalIpAddress(Unknown Source)
        at org.gudy.azureus2.pluginsimpl.local.utils.UtilitiesImpl.getPublicAddress(Unknown Source)
        at com.aelitis.azureus.core.dht.transport.udp.impl.DHTTransportUDPImpl.getExternalAddress(Unknown Source)
        at com.aelitis.azureus.core.dht.transport.udp.impl.DHTTransportUDPImpl.<init>(Unknown Source)
        at com.aelitis.azureus.core.dht.transport.DHTTransportFactory.createUDP(Unknown Source)
        at com.aelitis.azureus.plugins.dht.impl.DHTPluginImpl.<init>(Unknown Source)
        at com.aelitis.azureus.plugins.dht.DHTPlugin$7.runSupport(Unknown Source)
        at org.gudy.azureus2.core3.util.AEThread.run(Unknown Source)
```

And similar errors.

Also when trying to use the swingUI, I get these errors:

```
Error Occured
java Applet Window
(X) org/gudy/azureus2/core3/internat/MessageText

```

when launching through the applet tag and

```

Error Occured
java Applet Window
(x) java.lang.NoClassDefFoundError

```
when launching via object with nested embedded tag.

The pages load but most of the lists and buttons are invisible unless you click on them....

Any ideas anybody?

Keep in mind that I am configuring over ssh, so CLI tools would be better....

Thanks

---

### Post by ubuntme on 2005-09-27
ok, I figured out that I hadn't set up the networking properly.

ubuntu didn't like me switching from wireless to wired, for some reson.  After swithing wireless off it is happier.

So the console ui is now working.

the swingui is still not working however....

---

