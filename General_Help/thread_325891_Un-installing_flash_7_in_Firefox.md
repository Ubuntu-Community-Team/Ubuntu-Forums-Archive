---
title: "Un-installing flash 7 in Firefox?"
date: 2006-12-26
forum: General Help
---

### Post by Redeyes_Gambit on 2006-12-26
}{i,

I'm trying to use the flash player 9 beta plugin for firefox 2.0, but despite the fact I have properly installed the plugin file, Firefox is defaulting to flash player 7. How do I disable/un-install the flash player 7 plugin for firefox? Sadly, I cannot remember if I used automatix (version 1 something) to install flash 7 or if I installed it via the standard Linux installer provided by adobe. I also have opera installed and would like to keep flash player 7 for it (as 9 is not yet stable in opera.) Last but not least I am using Ubuntu Dapper Drake.

Many thanks!

---

### Post by bruenig on 2006-12-26
> **Redeyes_Gambit said:**
> }{i,

I'm trying to use the flash player 9 beta plugin for firefox 2.0, but despite the fact I have properly installed the plugin file, Firefox is defaulting to flash player 7. How do I disable/un-install the flash player 7 plugin for firefox? Sadly, I cannot remember if I used automatix (version 1 something) to install flash 7 or if I installed it via the standard Linux installer provided by adobe. I also have opera installed and would like to keep flash player 7 for it (as 9 is not yet stable in opera.) Last but not least I am using Ubuntu Dapper Drake.

Many thanks!

Opera, at least the ubuntu debs of it, use the firefox plugin directory so unless you can find away around that, having them both installed is probably going to be a problem.

To uninstall flash 7, first do
```
sudo apt-get remove flashplugin-nonfree
```
which will remove it if you installed a deb

Then do
```
sudo rm /usr/lib/firefox/plugins/libflashplayer.so /usr/lib/firefox/plugins/flashplayer.xpt
```

which will remove it if you installed it manually.

If you aren't sure just do both of them in that order and there is no way you could damage anything, also see my signature for a full how to.

---

### Post by Redeyes_Gambit on 2006-12-27
Sadly, neither of those worked. I apparently didn't install it via a .deb because it wasn't listed as installed in synaptic, and the flashplayer.xpt/.so were not in the specified locations (or in "Mozilla" or "Mozilla Firefox" either for that matter)

Any more suggestions?

---

### Post by Redeyes_Gambit on 2006-12-28
Anybody?

---

### Post by HadroLepton on 2006-12-28
type **about:plugins** in the firefox address bar. it should list all plugins which are installed in your browser. look for the flash plugin and check where the *.so file is located. then take measures to remove that file. don't forget to restart firefox

---

### Post by Redeyes_Gambit on 2006-12-28
Already looked there, that's how I figured out both flash 7 and flash 9 were installed. It doesn't list the location of any of the files (It would make it too easy ;) )

---

### Post by HadroLepton on 2006-12-29
try this [http://kb.mozillazine.org/About:plugins](http://kb.mozillazine.org/About:plugins)
> To show the full path instead of just the name of each plugin file, type about:config in the address bar and press Enter. Find the preference plugin.expose_full_path and change the value to "true" (double-clicking the preference name will toggle the setting).


seems like the default setting does not show the paths to the plugins.

---

### Post by Redeyes_Gambit on 2006-12-30
AHA! The sneaky little plugin was lurking in a hidden ".Mozilla" folder in my home directory! The plugin files have been eliminated. Flash 9 is working, woohoo! Many thanks! :)

---

