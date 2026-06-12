---
title: "I cant install plugins (java/mplayer) for firefox/mozilla"
date: 2007-06-18
forum: General Help
---

### Post by knubbe on 2007-06-18
Hi,

I'm trying to install java plugin for my firefox browser. The apt-part of the installation went smooth (sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-fonts), but when i try to visit a page with a java applet, it says i have to install the java plugin.

Since it didn't work, i lost interest and i havent bothered until now when i really need to have java support (a swedish standard for online identification is using a java applet).

I've also tried installing mplayer, and i have the same problem there; the apt-part says it's OK, but when i try to watch a movie in firefox it says i need to install mplayer.

Can there be something wrong with my ~/.mozilla? Im not sure how the rights should be set, but i can see my user is the owner.

I've installed firefox via the repos and then i've installed swiftfox via their shell-script (install-swiftfox.sh or similar). I'm using Kubuntu 7.04 (fresh install this time, no upgrade - but it was installed when 7.04 was the final beta).

All help is appreciated. Thanks!

Knubbe

---

### Post by jscudder on 2007-06-18
In the address field at the top of Firefox, type "about:plugins" (without the quotes).  This will give you a list of all the plugins that are installed.  

For Firefox to see a plugin, the actual plugin or a link to the plugin has to be in one of three places:  .mozilla/plugins, /usr/lib/mozilla/plugins, or /usr/lib/firefox/plugins .  The actual java plugin resides in /usr/lib/jvm/java-6-sun/jre/plugin/i386/ns7/libjavaplugin_oji.so. So all you need to do is create a link from that location to one of your Firefox plugin locations.  

You can do this with Nautilus by opening up 2 windows, one for /usr/lib/jvm/java-6-sun/jre/plugin/i386/ns7  and one for .mozilla/plugins.  Drag the libjavaplugin_oji.so file from  /usr/lib/jvm/java-6-sun/jre/plugin/i386/ns7 while holding down the ALT key and place in the .mozilla/plugins window by selecting 'Link Here'.

You can also do this from the command line by opening a terminal window and typing 'ln -s /usr/lib/jvm/java-6-sun/jre/plugin/i386/ns7/libjavaplugin_oji.so .mozilla/plugins/libjavaplugin_oji.so'  (without the quotes). To save typing all that, Copy and Paste that line from here to your terminal window.

To check to see if your plugin has been installed, open Firefox and type 'about:plugins'

John

---

### Post by knubbe on 2007-06-23
> **jscudder said:**
> In the address field at the top of Firefox, type "about:plugins" (without the quotes).  This will give you a list of all the plugins that are installed.  

For Firefox to see a plugin, the actual plugin or a link to the plugin has to be in one of three places:  .mozilla/plugins, /usr/lib/mozilla/plugins, or /usr/lib/firefox/plugins .  The actual java plugin resides in /usr/lib/jvm/java-6-sun/jre/plugin/i386/ns7/libjavaplugin_oji.so. So all you need to do is create a link from that location to one of your Firefox plugin locations.  

You can do this with Nautilus by opening up 2 windows, one for /usr/lib/jvm/java-6-sun/jre/plugin/i386/ns7  and one for .mozilla/plugins.  Drag the libjavaplugin_oji.so file from  /usr/lib/jvm/java-6-sun/jre/plugin/i386/ns7 while holding down the ALT key and place in the .mozilla/plugins window by selecting 'Link Here'.

You can also do this from the command line by opening a terminal window and typing 'ln -s /usr/lib/jvm/java-6-sun/jre/plugin/i386/ns7/libjavaplugin_oji.so .mozilla/plugins/libjavaplugin_oji.so'  (without the quotes). To save typing all that, Copy and Paste that line from here to your terminal window.

To check to see if your plugin has been installed, open Firefox and type 'about:plugins'

John
Thanks, now java works here. Do you know which .so-file to use for mplayer?

---

### Post by cookies on 2007-06-23
mplayerplug-in-dvx.so for DivX
mplayerplug-in-qt.so for QuickTime
mplayerplug-in-wmp.so for Windows Media Player
mplayerplug-in.so for all other types of multimedia

EDIT: mplayerplug-in.so also does RealPlayer, but it doesn't work so well, so don't use it for RealPlayer.

---

### Post by dakochan on 2007-06-24
Hi,

I have a question about firefox plugin.
In the beginning I installed ubuntu with Totem as default, as a stand alone player and as a firefox plugin player.
But, I want to try mplayer as firefox plugin.
I've installed mplayer plugins for firefox. But, when play any movie in firefox (quicktime), the plugin from totem is used automatically. I saw in "about:plugins", I saw the plugins from mplayer and totem.

So, how to change the default plugins for movie player in firefox ?

Best Regards,
Dakochan

---

