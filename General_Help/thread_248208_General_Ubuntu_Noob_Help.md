---
title: "General Ubuntu Noob Help"
date: 2006-08-31
forum: General Help
---

### Post by TheReconHunter on 2006-08-31
Hey, I just installed ubuntu, and already I love it. Within 2 days of getting ubuntu, its pretty safe to say windows will be collecting dust now.

However, I have a few questions for the community. First off, I downloaded EasyUbuntu and Automatix, to hopefully integrate some familiar programs to linux. I just wanted to know are there any more essential plugins or applications that I should consider downloading, either because I need them or they are just really awesome.

Also, regarding movies and music, are there any music players out there better than Rhythmbox? It doesnt support my multimedia keyboard functions, and thats kind of annoying. Also, all my music and movies are on my ntfs hard drive, and that means opening up windows to acess it. Is it possible with Rhythmbox, or any other more powerful linux media player to acess these files? (I havent tried yet, as my main priority is to hopefully upgrade from Rhythmbox).


I know its against practice to start a vague thread like this, but I am kind of alone in the linux world. :???: Much thanks to anyone who responds to this thread, and sorry if it was posted in the wrong area etc.

---

### Post by Anonii on 2006-08-31
I'll answer to the audio player question.
If you are using KDE, I would propose you Amarok. But I guess you are using GNOME. I'd recommend you Banshee, I liked it more than Rhythmbox.
Also, your keyboard shortcuts can be configured with:

System -> Preferences -> Keyboard Shortcuts

Also to access the files doesnt depend on the player, but on the user :)
You can, but I will leave this to someone else, because havent really used windows for a year or so... and I'm not sure what you have to do ^_^

---

### Post by TheReconHunter on 2006-08-31
Thanks. I also found this [top 10 ubuntu tweaks guide]("http://lifehacker.com/software/ubuntu/hack-attack-top-10-ubuntu-apps-and-tweaks-195437.php") and the number 10 suggestion (which I notice there is a thread of) looks really awesome. But sadly, I have an additional 2 problems. For some reason, sound on youtube (didnt try other flash applets) doesn't work, and also, when I try installing alot of apps, I get an error message as follows:

chris@chris-desktop:~$ apt-get install amarok
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?


Any feedback on these new problems or my original question with ntfs would be greatly appreciated. Much thanks.

---

### Post by Anonii on 2006-08-31
Obviously you are not root ^_^ Root is the superuser. The mastah of everything in Linux. THE GOD!

To become root for a single command use this:


sudo aptitude install amarok

And now you will read this:
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)
and this:
[http://monkeyblog.org/ubuntu/installing.html](http://monkeyblog.org/ubuntu/installing.html)

---

### Post by skymt on 2006-08-31
I suggest Quod Libet as a jukebox. If you also install quodlibet-plugins, you get multimedia key support. I won't go into why Quod Libet is so great, just check out the [website](http://www.sacredchao.net/quodlibet). It may have fewer features than Amarok, but in my opinion it has more *useful* features. Who actually uses Amarok's Wikipedia lookup or moodbar?

---

### Post by Anonii on 2006-08-31
> **skymt said:**
> I suggest Quod Libet as a jukebox. If you also install quodlibet-plugins, you get multimedia key support. I won't go into why Quod Libet is so great, just check out the [website](http://www.sacredchao.net/quodlibet). It may have fewer features than Amarok, but in my opinion it has more *useful* features. Who actually uses Amarok's Wikipedia lookup or moodbar?
I did, to be honest :P

And I also prefered Banshee from Quod Libet. I was using Quod for a while, but changed after a format :3

Check Banshee here, btw:
[http://banshee-project.org/Main_Page](http://banshee-project.org/Main_Page)

---

### Post by orb9220 on 2006-08-31
You can use amarok in gnome you don't have to run kde to run kede apps in gnome.

For keyboard support thier is a program for all those multimedia keyboards out there it is called keytouch. [http://keytouch.sourceforge.net/](http://keytouch.sourceforge.net/)

for latest amarok 1.4.2 open a term and entry each command:

wget [http://people.ubuntu.com/~jriddell/kubuntu-packages-jriddell-key.gpg](http://people.ubuntu.com/~jriddell/kubuntu-packages-jriddell-key.gpg)

sudo -s

apt-key add kubuntu-packages-jriddell-key.gpg

echo "deb [http://kubuntu.org/packages/amarok-latest](http://kubuntu.org/packages/amarok-latest) dapper main" >> /etc/apt/sources.list

apt-get update

apt-get install amarok amarok-engines

---

### Post by Anonii on 2006-08-31
Of course, you dont have to have KDE to use GNOME apps, _but_ to use Amarok, you will have to load the Qt libraries too, and that greatly reduces the performace. Also the Qt graphics doesnt appear correctly, in GNOME. :(
I generally, dont recommend Amarok on GNOME :/

---

### Post by TheReconHunter on 2006-08-31
Is it possible to somehow uninstall keytouch? For some reason, Ubuntu is acting all screwy now, and the keytouch homepage is now my default homepage... wtf?

---

### Post by strabes on 2006-09-15
sudo apt-get remove keytouch

:) :) :) It makes me happy when I see a new linux user!!!

I would definitely recommend installing XGL/Compiz. It seems to be much more stable now than in the past. Here's a guide: [http://www.compiz.net/viewtopic.php?id=389](http://www.compiz.net/viewtopic.php?id=389)

Don't follow the 'normal' how to, instead do the second one, that way you can always go back to a normal gnome session in case XGL messes up, and IMHO it seems to work better anyway.

---

### Post by canadianwriterman on 2006-09-15
I love Rhythmbox and imported my Windows music files from my Windows drive using Music > Import Folder from within Rhythmbox. Then I simply navigated to where my music files were.

---

