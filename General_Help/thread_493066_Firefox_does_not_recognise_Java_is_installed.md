---
title: "Firefox does not recognise Java is installed"
date: 2007-07-05
forum: General Help
---

### Post by Game_boy on 2007-07-05
After installing Java through Synaptic Firefox cannot find the plugin. Firefox's help website says Java should work if I "change to my plugins directory" but gives no indication of where or how.

---

### Post by moore.bryan on 2007-07-05
[I]from the [java site]("http://java.com/en/download/help/5000010500.xml#enable"):
[/I]>  **Mozilla 1.4 and later **[LIST=1]
[*]Go to the plugins sub-directory under the Mozilla installation directory
    **cd <Mozilla installation directory>/plugins**
[*]In the current directory, create a symbolic link to the JRE **ns7**/libjavaplugin_oji.so file Type:
    ln -s <JRE installation directory>/plugin/i386/**ns7**/libjavaplugin_oji.so
_Example:_[LIST]
[*]If Mozilla is installed in this directory:
        **/usr/lib/mozilla-1.4/**
[*]and if the JRE is installed at this directory:
        **/usr/java/jre1.5.0**
[*]Then type at the terminal to go to the browser plug-in directory:
        **cd /usr/lib/mozilla-1.4/plugins**
[*]Enter the following command to create a symbolic link to the Java Plug-in for the Mozilla browser.
          [B]ln -s /usr/java/jre1.5.0/plugin/i386/ns7
        /libjavaplugin_oji.so .[/B][/LIST] 
[*]Start Mozilla browser or restart it if it is already running. Note that if you have other Mozilla components (ie: Messenger, Composer, etc) running, you will need to restart them as well.
[*]Go to **Edit** > **Preferences**. Under **Advanced** category > Select **Enable Java**[/LIST][I]
stupid symlinks... 
;-)
[/I]

---

### Post by stchman on 2007-07-05
> **Game_boy said:**
> After installing Java through Synaptic Firefox cannot find the plugin. Firefox's help website says Java should work if I "change to my plugins directory" but gives no indication of where or how.

Install java this way:

sudo apt-get install sun-java5-bin sun-java5-jre sun-java5-jdk sun-java5-fonts sun-java5-plugin

The sun-java5-plugin will be the one that Firefox uses.

Make sure you uninstall the old Java stuff.

---

