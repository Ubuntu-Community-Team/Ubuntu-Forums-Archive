---
title: "TrueCrypt Won't Run Under 14.04 or 16.04"
date: 2018-04-30
forum: General Help
---

### Post by giddyup3062 on 2018-04-30
Hello, and thanks in advance.

First I know the program is not officially supported anymore. It has worked almost flawlessly until I did an update with 14.04. It gave me some pop-up about "net neutreality". It even had problems updating via terminal. I had to use apptitude. I then restarted my computer several times. I decided to upgrade to 16.04 to see if it would work. In 14.04 and 16.04 it shows that it is running, but the GUI doesn't pop up. I have about 20 years of data on there, and some pics and vids cannot be replaced. The only problem I've had is I have to use rm ~/.TrueCrypt-lock-billy every once in a while. I did some research last night, and wasn't able to find anything useful out.


Kind Regards,

Mike

---

### Post by speartip on 2018-05-01
Try using Veracrypt instead.
[https://www.veracrypt.fr/en/Downloads.html](https://www.veracrypt.fr/en/Downloads.html)
I'm certain it's compatible with truecrypt & it's actively developed.
Works perfectly on 16.04.

---

### Post by giddyup3062 on 2018-05-01
Thanks for the reply [**[COLOR=#000000]speartip[/COLOR]**]("https://ubuntuforums.org/member.php?u=1776664")1 I appreciate it! However I am bamboozled as to how I got it to work. I didn't realize 18.04 was out, so I upgraded. Still says 16.04 LTS. After "upgrading" it would only let me use the keyboard to log in. After I restarted the computer via hard restart, it would let me use the aarow keys. Two known working keyboards, and two known working mouses failed. After over half a dozen restarts, one keyboard worked, and TruCrypt worked fine! I am confused about why/how I've had so many problems. I'm far from being Linus Torvalds, or Richard Stallman, but I've been using Ubuntu for about 10 years.

---

### Post by speartip on 2018-05-01
I think your problems probably stem from the upgrade.
Any 3rd party apps (TrueCrypt being one of them) can cause issues after an upgrade. I've also had issues in the past after upgrading. That's why a fresh install is usually recommended. It causes a bit more work, but I find it's worth it.
Anyway if TrueCrypt is now working, all's good.

---

