---
title: "bah-boom, bah-boom noise won't cease!"
date: 2019-08-05
forum: General Help
---

### Post by oldjazzcat on 2019-08-05
After reading How To Geek’s article on the upcoming demise of Windows 7 on Jan. 14, 2020 and if you don’t want to use Windows 10, that’s fine—you should consider a Chromebook, Mac, iPad, or just installing Linux on your current PC. 

After a good deal of research, I installed a dual boot with Windows7, and Ubuntu 18.04.02LTS on my old desk top. All has been going well; learning the new software, dabbling with the command line interface and finding, installing and learning new substitutes for the Window programs I used for my daily work. I’ve progressed to the point of using Ubuntu about 90% of the time.

I notice during the boot up procedure a  bah-boom,  bah-boom noise, which I took as being similar to Windows chimes sound at boot up.  I also noticed receiving Ubuntu updates on a regular basis, which I would always install.
After complying to such a software upgrade notice and re-booting I heard the usual bah-boom noise, which usually stops after a few rounds; but this time it continues and is very ignoring. 

Since this started after one of the updates and since it seems to be an extension of the boot up notification sound, I suspect the last update somehow corrupted my boot system. I have re-booted many times and the noise continues. I have run apt-get upgrade and it says my system is up to date. How can I correct this problem?

Thank you for any advice, Ronald L Gable

---

### Post by pickled-potato on 2019-08-05
Could you include a screenshot of startup applications?

---

### Post by dragonfly41 on 2019-08-05
There is this [sound troubleshooting guide]("https://help.ubuntu.com/community/SoundTroubleshootingProcedure").

Presumably [the ideas here]("https://askubuntu.com/questions/1162983/bah-boom-bah-boom-noise-wont-cease") did not work?

---

### Post by mastablasta on 2019-08-05
kernel got upgraded. kernel in linux includes drivers. if you think it's a bug report it to launchpad, so they can fix it for the next update.

turn off star up sound or as suggested in the link delete the file.

---

### Post by oldjazzcat on 2019-08-12
Thanks to all foryour suggestions, unfortunately I still have the bah-boom, bah-boomnoise.  I tried some of the suggestions and some were a bit over myhead but no solutions. I do have a couple of workarounds &#8211; thefirst; as long as I stream music the drum noise ceases even if turnthe music volume all the way down and the other way is to to turn myspeakers off.


Additional notes &#8211;using the workarounds, I cannot detect any other computing problemand when I boot into Windows 7 there is no drum beat noise.


After more research,I&#8217;m thinking about trying to reinstall Grub or upgrade to Ubuntu18.04.3LTS. I&#8217;m trying to proceed with caution because I don&#8217;twant to lose all the work on my system, although I believe it&#8217;s allbacked up. &#8211; Any comments or suggestions would be appreciated.

---

### Post by mastablasta on 2019-08-13
> **oldjazzcat said:**
> 
After more research,I’m thinking about trying to reinstall Grub or upgrade to Ubuntu18.04.3LTS. I’m trying to proceed with caution because I don’twant to lose all the work on my system, although I believe it’s allbacked up. – Any comments or suggestions would be appreciated.


upgrading could work and it is safe since you will upgrade only kernel & drivers. 

if it all works well on windows then the issue is drivers for the sound chip. the error might have been resolved in new kernel or not. 

i had strange sound issues (no output) since 9.10 and found that reloading alsa often solved them. not always, so sometimes a shutdown and another boot was required by turning off the current for about 15 seconds during the process.
anyway with 18.04 (after 9 years!) the issue is gone and hasn't resurfaced since. so obviously someone fixed the driver.

---

