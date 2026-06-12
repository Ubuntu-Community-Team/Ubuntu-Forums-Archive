---
title: "One-click Java 8 install?"
date: 2015-02-20
forum: General Help
---

### Post by Q-collective on 2015-02-20
I'm in the midst of setting up a small business to support Ubuntu home desktop users and I've opted to use [ScreenConnect]("http://screenconnect.com/") for remote login. However, it uses Java to be crossplatform, which is not installed by default on Ubuntu.

Now, I'm aware of [this little how to]("http://www.webupd8.org/2012/09/install-oracle-java-8-in-ubuntu-via-ppa.html") to install Java 8, but given my initial audience being the novice userbase, this might be a little daunting for quite a few. So, I'm looking to streamline this install process.

I could of course put the *automated installation* part of that how to in a little downloadable script, but maybe there are even better ways? That's my question :)

---

### Post by nerdtron on 2015-02-20
Does it really need Java 8 specifically? The iced tea java alternative from the software center works for me on my Java needs.

```

kenneth@nerdtron:~$ apt-cache search icedtea
icedtea-7-jre-jamvm - Alternative JVM for OpenJDK, using JamVM
icedtea-7-plugin - web browser plugin based on OpenJDK and IcedTea to execute Java applets
icedtea-netx - NetX - implementation of the Java Network Launching Protocol (JNLP)
icedtea-netx-common - NetX - implementation of the Java Network Launching Protocol (JNLP)
icedtea-plugin - web browser plugin to execute Java applets (dependency package)


```

If it runs on the above packages then your can just sudo apt-get install package on other computers to set it up.

---

### Post by Q-collective on 2015-02-20
I could test that out. Thanks, I'll get back at you.

---

### Post by Q-collective on 2015-02-20
Ok, I've put a link to [http://apt.ubuntu.com/p/icedtea-7-plugin](http://apt.ubuntu.com/p/icedtea-7-plugin) on the session page, which leads you to the Ubuntu Software Center and you only have to click 'install', close the USC, close the tab to that apt link and click again on the session button to now have Firefox open the jnlp file with the plugin.

This workflow is simple enough for a directed phone support situation :)

---

