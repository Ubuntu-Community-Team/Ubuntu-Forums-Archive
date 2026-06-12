---
title: "kubuntu is not good"
date: 2007-11-09
forum: General Help
---

### Post by LeonLanford on 2007-11-09
kubuntu 7.10 gutsy ribbon cd arrived yesterday.. i was so happy that i want to try install it, i already prepared my laptop for this :-D

the instal was completed successfully without any error.. but the problem is when i'm using kubuntu.

1. when booting and shutdown, there is no other thing than black screen! when i'm using knoppix it shows processes booting up or shutdown, when i'm using mandriva it shows some splash screen loading, when i searched about it, it's problem from kubuntu itself.. some people are lucky enough to get it repaired, i'm the unlucky one, i already followed the trick in the ubuntu forum but still cannot solve this case -> [http://ubuntuforums.org/forumdisplay.php?f=131](http://ubuntuforums.org/forumdisplay.php?f=131)

2. gedit  doesn't work, always got error problems..

3. wine emulator error and cannot be installed! i wonder why..

4. sometimes the system crash when i open certain folders.. (an error box opened)

5. not many applications and other applications cannot be installed! i tried to instal some of the applications but failed..

i don't know if other people encounter my problem.. is this because i'm using free shipit cd?

---

### Post by g2g591 on 2007-11-09
hmm that is indeed strange behavior, do you see the loading screen when you boot up? as for other Kubuntu users encountering the problem, personally I do not.
2. gedit is gnome editor, and is not installed in Kubuntu, kate is the kde equivalent
3. did you try installing the version from [www.winehq.org]("http://www.winehq.org") ? that has the latest version
4.no idea whats wrong there
5.or here
try putting your cd in the drive (and rebooting) and verify the disk
If you have at least 128k internet, id recommend trying buring your own disk if the shipit one was bad
have to leave not able to reply more for 30min

---

### Post by LeonLanford on 2007-11-09
> **g2g591 said:**
> hmm that is indeed strange behavior, do you see the loading screen when you boot up? as for other Kubuntu users encountering the problem, personally I do not.
2. gedit is gnome editor, and is not installed in Kubuntu, kate is the kde equivalent
3. did you try installing the version from [www.winehq.org]("http://www.winehq.org") ? that has the latest version
4.no idea whats wrong there
5.or here
try putting your cd in the drive (and rebooting) and verify the disk
If you have at least 128k internet, id recommend trying buring your own disk if the shipit one was bad
have to leave not able to reply more for 30min

thanks for the reply..

1. you know that many people here encountering same problem.. :D
2. ow i don't know gedit is gnome editor, sorry..
3. haven't tried, i don't know that site.. (edit) wew i must use internet connection to download it? my laptop doesn't have internet connection.. ```
For Ubuntu Gutsy (7.10):
sudo wget http://wine.budgetdedicated.com/apt/sources.list.d/gutsy.list -O /etc/apt/sources.list.d/winehq.list

For Ubuntu Feisty (7.04):
``` while mandriva wine can be downloaded.. -> [http://sourceforge.net/project/showfiles.php?group_id=6241&package_id=80066](http://sourceforge.net/project/showfiles.php?group_id=6241&package_id=80066)
5. when the application ask to put cd, i put the cd but some error mesages said that i cannot instal the applications.. this goes to wine as well..

my internet is so lame that i need to request free cd..and i don't have credit card or something to buy..

---

### Post by g2g591 on 2007-11-09
can you list some of the error messages? and did you verify the cd (boot from it almost like you did from install, and on the very first menu hit verify cd) and you should be able (from windows or another computer) go to packages.ubuntu.org and download a .deb file , which u can burn to cd and then transfer over to ubuntu where you should be able to simply double click to install.
have to leave again (for 2 hrs)

---

### Post by LeonLanford on 2007-11-11
sorry for the delay..

i don't have cd burner.. :(

ok i'll explain my errors..

[[IMG]http://img139.imageshack.us/img139/2246/snapshot1rv4.th.png[/IMG]](http://img139.imageshack.us/my.php?image=snapshot1rv4.png)

it said my wine is not instaled but when i see in in add/remove program section, the wine is already there.., after i clicked yes, this is what happened

[[IMG]http://img204.imageshack.us/img204/5222/snapshot2jl3.th.png[/IMG]](http://img204.imageshack.us/my.php?image=snapshot2jl3.png)
[[IMG]http://img127.imageshack.us/img127/6159/snapshot3og5.th.png[/IMG]](http://img127.imageshack.us/my.php?image=snapshot3og5.png)

i sometimes get this error messages, not just when try to install wine..




[[IMG]http://img116.imageshack.us/img116/476/snapshot4yt1.th.png[/IMG]](http://img116.imageshack.us/my.php?image=snapshot4yt1.png)

in this image as you can see many applications not instaled and cannot be installed, i cannot click it.. i tried to instal from cd but not found anything like menu to instal, even gimp is not installed..


my friend said to use command 'apt-get install', i tried that and found this error

[[IMG]http://img108.imageshack.us/img108/5999/snapshot5on4.th.png[/IMG]](http://img108.imageshack.us/my.php?image=snapshot5on4.png)



when i closed the file browser i **always** get this error no matter what folder i open

[[IMG]http://img267.imageshack.us/img267/533/snapshot6ao2.th.png[/IMG]](http://img267.imageshack.us/my.php?image=snapshot6ao2.png)


and the last thing.. 'cut' command not working in linux.. i cut these screenshot but the files were still there.. i must delete manually, in knoppix 'cut' command is working.. so what's the function 'cut' in kubuntu?


edit : i forgot to say, i tried these things in normal mode and root mode

i guess this the price i must pay for free live cd?

---

### Post by tacutu on 2007-11-11
this has nothing to do with the free cd. As you were told, you should put the cd in the cd-drive, start the computer and select the "test installation media". If you get any errors, it means the cd is somehow damaged and you need a different one. If you don't have a fast enought internet coneection, you can go to an internet cafe and download/burn if from here (i did that in the old days). 

However, my personal hunch is that you somehow messed the installation and should perhaps try to reinstall ubuntu from scratch. 

Since you don't have an internet connection on your laptop, you also might have to set up a local repository for software, from which you could install any extra applications you need. Just search the forums for how to do that.

---

### Post by LeonLanford on 2007-11-11
> **tacutu said:**
> this has nothing to do with the free cd. As you were told, you should put the cd in the cd-drive, start the computer and select the "test installation media". If you get any errors, it means the cd is somehow damaged and you need a different one. If you don't have a fast enought internet coneection, you can go to an internet cafe and download/burn if from here (i did that in the old days). 

However, my personal hunch is that you somehow messed the installation and should perhaps try to reinstall ubuntu from scratch.

i already put the cd in the drive.. already tested the cd, i request 2 cds in case one cd is broken down but the second cd did the same..  internet cafe here is expensive and also slow and to download 600mb of files will take half day..

> **tacutu said:**
> 
Since you don't have an internet connection on your laptop, you also might have to set up a local repository for software, from which you could install any extra applications you need. Just search the forums for how to do that.

i don't understand.. sorry my english is bad..



i just want to test kubuntu because many people said it's good and it provide free shipit cd.., but i get these errors, if i can't solve these errors i think i'll use other distro..

---

### Post by g2g591 on 2007-11-13
well, if you have language issues there are forums in other languages. see [http://www.ubuntu.com/support/community/webforums](http://www.ubuntu.com/support/community/webforums) and there also irc channels in different languages.

---

### Post by LeonLanford on 2007-11-13
my language is not there.. (indonesian)

i just solved one problem, the booting and shutdown screen but still have other errors..

---

