---
title: "BBC i player in Firefox"
date: 2008-03-27
forum: General Help
---

### Post by KMJones1 on 2008-03-27
I tried to use the BBC player in Firefox and it said I needed the Real Player. I have downloaded the file RealPlayer10GOLD.bin but it won't install (yes I have execute rights, and the result is: "bash: ./RealPlayer10GOLD.bin: No such file or directory" even though the file is there!)
I tried the Helix .rpm file but that wouldn't install, then I see that the Helix files only seem to work on x86 systems. I have an AMD 64 bit system; is that the trouble I wonder?
I am fully updated with Ubuntu 7.10 and Firefox 2.0.
Thanks for any ideas

---

### Post by AlanR8 on 2008-03-27
This is what I do.

I don't download anything to do with Real Player. I download the Mplayer Mozilla plug in, that also installs Mplayer. I also install the flash plug in. Both are available in the repros. Being an old Doze hand, I then reboot and enjoy watching the unmissable!

---

### Post by KMJones1 on 2008-03-27
Thanks for those ideas.
I installed them from Synaptic OK. They seemed reluctant to work, but they are now OK!
Thanks very much.

---

### Post by ibuclaw on 2008-03-27
BBC iPlayer uses Adobe Flash Player. Does it not?

[Reference is found here.]("http://iplayersupport.external.bbc.co.uk/cgi-bin/bbciplayer.cfg/php/enduser/std_adp.php?p_faqid=243&p_created=1197394977&p_sid=UIuDwN_i&p_accessibility=0&p_redirect=&p_lva=30&p_sp=cF9zcmNoPTEmcF9zb3J0X2J5PSZwX2dyaWRzb3J0PSZwX3Jvd19jbnQ9MTImcF9wcm9kcz0mcF9jYXRzPTEwJnBfcHY9JnBfY3Y9MS4xMCZwX3BhZ2U9MQ**&p_li=&p_topview=1&cat_lvl1=10")

Adobe Flashplayer can be installed through the Multiverse Repository

```
 sudo apt-get install flashplugin-nonfree 
```

Regards
Iain

---

### Post by AndyCooll on 2008-03-27
> **tinivole said:**
> BBC iPlayer uses Adobe Flash Player. Does it not?

[Reference is found here.]("http://iplayersupport.external.bbc.co.uk/cgi-bin/bbciplayer.cfg/php/enduser/std_adp.php?p_faqid=243&p_created=1197394977&p_sid=UIuDwN_i&p_accessibility=0&p_redirect=&p_lva=30&p_sp=cF9zcmNoPTEmcF9zb3J0X2J5PSZwX2dyaWRzb3J0PSZwX3Jvd19jbnQ9MTImcF9wcm9kcz0mcF9jYXRzPTEwJnBfcHY9JnBfY3Y9MS4xMCZwX3BhZ2U9MQ**&p_li=&p_topview=1&cat_lvl1=10")

Adobe Flashplayer can be installed through the Multiverse Repository

```
 sudo apt-get install flashplugin-nonfree 
```

Regards
Iain
Correct. The BBC iPlayer doesn't require Real Player, or for that matter Windows Media Player. Certain video clips on the BBC website might do however, but these are separate from those of the BBC iPlayer service.

And although you've installed the mozilla-mplayer plugin, that was actually unecessary since the website clips work perfectly ok with the (already installed) Totem mozilla-plugin and then choosing the Windows Media player format. All that you might have been required to get it working properly was to install additional gstreamer codecs.
  
:cool:

---

### Post by KMJones1 on 2008-03-28
Thanks for these.
I had installed the flashplayer OK.
It isn't working at the moment. Clicking Winows Media produces a small window "XINE buffering 10%"  with action bar showing "read sync.bbc.co.uk" then "xine plugin - playback started". It then hangs. Buffering never gets over 10%.
Clicking the Real Player button has the same effect, but a start button and volume control appear, but have no effect.

---

### Post by KeyserSoze93 on 2008-03-28
is it the actual iplay or is it some other BBC watch again service ? I ask because the iplayer works fine for me in firefox but the clips related to "The City Speaks" do not since they use some different media system and they try and use the mplayer plugin (since that is what i have) and then just stop...

---

### Post by nedkelly on 2008-05-24
I have the flashplugin-nonfree install and it is used to play flash.
about:plugins says: "File name: libflashplayer.so Shockwave Flash 9.0 r124"

BUT I can still not play the news clips on the BBC News page. Any ideas?



EDIT: I found out it was because I had the adblock plugin activated

---

### Post by KMJones1 on 2008-05-25
I have just updated to Ubuntu 8.24 HH and BBC player works!!
Thanks to the developers.

---

