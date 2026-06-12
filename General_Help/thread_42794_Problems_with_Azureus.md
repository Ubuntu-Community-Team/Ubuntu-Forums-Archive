---
title: "Problems with Azureus"
date: 2005-06-19
forum: General Help
---

### Post by Aurelius on 2005-06-19
Azureus ran fine until the latest update. After the latest update, though, I get the following errors when trying to run it.

```
Exception in thread "main" java.lang.ExceptionInInitializerError
        at com.aelitis.azureus.core.impl.AzureusCoreImpl.<init>(AzureusCoreImpl. java:121)
        at com.aelitis.azureus.core.impl.AzureusCoreImpl.create(AzureusCoreImpl. java:69)
        at com.aelitis.azureus.core.AzureusCoreFactory.create(AzureusCoreFactory .java:46)
        at org.gudy.azureus2.ui.swt.Main.<init>(Main.java:35)
        at org.gudy.azureus2.ui.swt.Main.main(Main.java:98)
Caused by: java.lang.IllegalArgumentException: port out of range:66012
        at java.net.InetSocketAddress.<init>(Unknown Source)
        at java.net.InetSocketAddress.<init>(Unknown Source)
        at com.aelitis.azureus.core.networkmanager.impl.IncomingSocketChannelMan ager.start(IncomingSocketChannelManager.java:173)
        at com.aelitis.azureus.core.networkmanager.impl.IncomingSocketChannelMan ager.<init>(IncomingSocketChannelManager.java:103)
        at com.aelitis.azureus.core.networkmanager.NetworkManager.<init>(Network Manager.java:77)
        at com.aelitis.azureus.core.networkmanager.NetworkManager.<clinit>(Netwo rkManager.java:44)
        ... 5 more
```

I can see that the problem is with the port address, but I can't get into the program to change it, and I don't know where it stores that information.

---

### Post by Aurelius on 2005-06-19
Nevermind - it just hit me to check for hidden folders in my user directory. There was the .azureus folder, with a config file under it. Problem solved.

---

