---
title: "LibreOffice apps duplicating icons in the Unity launcher"
date: 2013-03-31
forum: General Help
---

### Post by Phantom010 on 2013-03-31
This is a relatively new problem. When clicking on any LibreOffice icons in the Unity launcher 3 times in a session, it will open a second icon in the launcher. Then, the initial icon will be impossible to remove (after second click) until a next reboot. When rebooted, all LibreOffice icons are gone, until I drag another one in there. Again, after clicking 3 times, it starts all over again, until reboot.

Any way to fix that?

Thank you

---

### Post by Phantom010 on 2013-03-31
Forgot to mention. I'm using Ubuntu 12.04 LTS, recently installed.

---

### Post by vanadium on 2013-03-31
It is not a new problem: Libreoffice and the Unity taskbar have never been flawless, although the current issues are not anymore the nightmare it once was. My current workaround is not to pin any Libreoffice icons. I find it easy enough to summon Libreoffice using the dash, and in 80% of the cases, I start LO by launching documents from the file manager anyway. One day, LO and Unity laucher will work properly together as designed.

The lack of hotkeys in the LO global menus is another issue: there, my workaround is (to my regret) to remove the global menu.

---

### Post by Phantom010 on 2013-03-31
Well, it may not be a new problem, but it seems to be for me and it's very disappointing. Such an obvious bug should have been dealt with a long time ago. Now I understand why people hate Unity so much. Will probably go with Mint with MATE desktop. Eye candy is always too unstable.

---

### Post by Phantom010 on 2013-03-31
I've also found that LibreOffice is not the only application doing this.

---

### Post by vanadium on 2013-04-01
Although I don't believe it, i am currently testing this: [https://sites.google.com/site/lightrush/random-1/howtofixduplicategnometerminalbyobuiconsintheunitylauncher](https://sites.google.com/site/lightrush/random-1/howtofixduplicategnometerminalbyobuiconsintheunitylauncher). According to that blog, there is a "wrong way" and a "right way" fixing icons to the laucher. I now added the LO icons the "right" way, i.e. by dragging them from the dash to the launcher, and opening and closing LO documents randomly to see whether and when the duplicate icon will appear. I must mention, though, that I am using 12.10.

---

### Post by Phantom010 on 2013-04-01
I believe the article is full of it. Both methods amount to the exact same result, which is nothing good. But thanks for the thought.

As soon as I've repartitioned my Windows XP (with software), I'm installing Mint. Unity is simply killing Ubuntu.

As a side note. I always run my applications maximized. In Ubuntu, you can't do that without ending up with your Exit button on the left. That's very irritating!

---

### Post by vanadium on 2013-04-02
I have done some extensive testing and have not yet reproduced the problem. It is thus possible that it now works well in my version of Unity. Beware that 12.04 is an older version of Unity, and Unity is evolving fast.

---

### Post by Phantom010 on 2013-04-02
12.04 is supported until 2017. That's why I didn't install version 12.10, which is probably even less stable. I'm not in the habit of reinstalling an OS every year.

---

### Post by speartip on 2013-04-02
Phantom...
I used to have this problem with LO on 12.04. Recently it has disappeared.
What version of LO are you using & is your system fully updated?

---

### Post by Phantom010 on 2013-04-02
Looks like I have version 3.5.7.2, which is probably the latest for Linux, as I keep everything up-to-date. There's version 4 on the site, but it might be for Windows. I noticed the problem after I inadvertently updated language packs (not only for LibreOffice), but it could be coincidence. 

Should I try uninstalling and reinstalling LibreOffice? How would I do that. When opening the Ubuntu Software Center, all LibreOffice programs seem to be separate. How can I remove LibreOffice globally? Then again, if it's like Windows, settings stay in the registry and when you reinstall, it's like you haven't changed anything.

Thanks.

---

### Post by speartip on 2013-04-02
I don't think uninstalling/reinstalling LO is the answer.
What I did was removed LO icons from the unity bar. Logged out & in again.
Opened LO writer from the dash & then pinned the icon again.
Logged out & in again & everything seemed fine.
Alternatively you could try the latest LO if you're feeling adventurous. I've been using it for a couple of weeks, with no issues.
You need to add the ppa as shown here:
[http://askubuntu.com/questions/252612/how-do-i-install-libreoffice-4](http://askubuntu.com/questions/252612/how-do-i-install-libreoffice-4)
I first uninstalled LO completely first.
```
sudo apt-get remove --purge libreoffice*
```
Then I installed the complete LibreOffice 4 from synaptic.

---

### Post by Phantom010 on 2013-04-02
I thought I already had the latest. Is the new one a Beta release?

---

### Post by Phantom010 on 2013-04-02
I'd really like to install LibreOffice 4, but damn, how do I do that?!? Synaptic? What to choose in there? There are tens or hundreds of entries for LibreOffice to check. Which one do I check? Why does everything have to be so complicated with Linux? Why not download and install, like Windows? Why not from the software manager? I was planning on going with Linux alone after the end of XP's support in April 2014. I'm having serious second thoughts! Linux is way too geeky for me! I consider myself an advanced Windows user, but this is ridiculous!

---

### Post by Phantom010 on 2013-04-02
Downloading from here:

[http://www.libreoffice.org/download/](http://www.libreoffice.org/download/)

---

### Post by Phantom010 on 2013-04-02
Incredible! I just can't figure it out! Man, what's wrong with downloading and clicking on an .exe file to install everything automatically? Geez!

Just can't find clear standard instructions anywhere! :mad:

There's just no easy straightforward way to do this, is there? This "change to DEB directory thing", how the heck do I do that? They tell us to do that, but not how!!! And then they tell us Linux is not really for geeks! Yeah, right...


> Right-click within the DEBS directory and choose *“Open in Terminal”*.  A terminal window will open. From the command line of the terminal  window, enter the following command (you will be prompted to enter your  root user's password before the command will execute):  sudo dpkg -i *.deb

There's no "Open to Terminal" to choose in there!!!

---

### Post by Phantom010 on 2013-04-02
Well, by messing around, I've deleted important files and my printer driver is useless. Why can't we install LibreOffice from the Software Manager, like many other programs? I'll have to go get my degree in rocket science if I want to pursue with Linux... 

I'm going to get rid of Ubuntu (installed with Wubi), and install Mint (with MATE desktop, of course). If I go through hell again with that distro, I'm forgetting about Linux and going with either Windows 8 or Blue in 2014. Linux is unfortunately not what I thought it was.

---

### Post by speartip on 2013-04-03
Phantom...
I will try to make this simple for you.
1st Delete existing libreoffice as in post 12.
2nd If you are installing from the downloaded .deb, which it appears you are, you need to either CD to the directory of the .debs or install a program called open-terminal: (recommended)
```
sudo apt-get install nautilus-open-terminal
```
You may need to logout/in for it to take effect.
3. Go to your downloaded .deb which is probably a .targz file. Right click it & "extract here"
4. Enter the .deb that you have extracted, inside there are 2 folders, enter the DEBS folder, then click "file" & "open in a terminal".
5. In the terminal type the command:
```
[COLOR=#2E8B57][FONT=Monaco]sudo dpkg -i *.deb[/FONT][/COLOR]
```
Wait for all the .debs to install.
6. Go back to your .deb folder & enter the "Desktop-integration" folder, click "file" & "open in a terminal" again.
7. Again type the command:
```
[COLOR=#2E8B57][FONT=Monaco]sudo dpkg -i *.deb[/FONT][/COLOR]
```
It' probably best to logout & in again at this point, but LO4 should now be installed.
 All the instructions are in this tutorial:
[http://forum.openoffice.org/en/forum/viewtopic.php?t=50119](http://forum.openoffice.org/en/forum/viewtopic.php?t=50119)

As far as a degree in rocket science goes, we probably all felt this way at one time, but bear with it, it does get easier, I promise.

---

### Post by Phantom010 on 2013-04-03
Thank you, my friend! :)

---

### Post by speartip on 2013-04-03
No problem.
Hope all is working well.

---

### Post by vanadium on 2013-04-03
Not sure, but I would presume that subscribing to the libreoffice 4 PPA would be a much easier solution to upgrade from the stock LibreOffice 3.6 to LibreOffice 4. See [http://askubuntu.com/questions/252612/how-do-i-install-libreoffice-4](http://askubuntu.com/questions/252612/how-do-i-install-libreoffice-4), first answer.

---

### Post by speartip on 2013-04-03
> **vanadium said:**
> Not sure, but I would presume that subscribing to the libreoffice 4 PPA would be a much easier solution to upgrade from the stock LibreOffice 3.6 to LibreOffice 4. See [http://askubuntu.com/questions/252612/how-do-i-install-libreoffice-4](http://askubuntu.com/questions/252612/how-do-i-install-libreoffice-4), first answer.

Vanadium...
I would agree & posted the ppa info in post 12, but the op went down the route of downloading the .deb from the official website, so I posted the installing info in my last post. PPAs are a lot easier though.

---

### Post by Phantom010 on 2013-04-03
Again, thank you for the info, but I've already got rid of Ubuntu. Not sure I will install another Linux distro again. However, if I do, it will be Mint, as Unity is not unanimous...

---

