---
title: "Problem with Automatix"
date: 2007-01-02
forum: General Help
---

### Post by kost@s on 2007-01-02
Hello guys,

I just installed through Automatix a program named Boot manager (i dont even remember the exact name of it  :( ) that was supposed to create a users spash in the beginning in the boot screen or sth like that. The thing is that when I rebooted my PC so that the changes take effect, Ubuntu starting screen was loaded OK and then, instead of leading me to the desktop, it gave me a kind of terminal screen whre I was asked to login with my username and pwd. After logging in, the terminal screen is still there and it seems that now all I can do is use commands. In other words it seems like I m somehow locked outside my desktop ](*,)  Do you know what program I talking about? I hope you do.... :(   Is there anyway to uninstall it by using commands or at least any way to access my desktop again? Thnx!

---

### Post by ajgreeny on 2007-01-02
Was it bootup-manager (or bum, as it's affectionately known)?  Once you've logged in in the terminal, type startx to see if a desktop appears.  If not then you may have stopped either gdm or other desktop manager, though I don't quite see how if you didn't run bum.

Did you also install an ati or nvidia graphic driver when you used automatix, because that may be the problem if you did.  If so in terminal, login then type:-
sudo dpkg-reconfigure xserver-xorg
which will let you reconfigure xorg and hopefully get everything working again.

---

### Post by arnieboy on 2007-01-02
FYI: This issue has been resolved in the Automatix forums:
[http://www.getautomatix.com/forum/index.php?showtopic=629](http://www.getautomatix.com/forum/index.php?showtopic=629)

---

### Post by wpshooter on 2007-01-06
I see in various posts on this forum and elsewhere, advising that to fix certain problems that a codecs32 needs to be installed.

Yet when I go into the Automatix 2 program, the very first thing I see is a WARNING that if I am in the United States (and I am) and that if I download and install this codecs32 program without paying someone for the rights, I am commenting a CRIME. 

I do not see any mention of who it is that I would purchase the rights to this program from .  Can someone tell me who this is ?

Also why is this program apparently free everywhere except the United States ?  

And if I could not pay for this program, what program would I use in it's place to get my operating system to properly perform certain functions that I need ?

Thanks.

---

### Post by Bullet666 on 2007-01-16
ok, i have tried every thing to get automatix to install. I have followed the directions on the automatix website, so i download the file, try and run it, but it won't open. It's the same with most programs i have tried to install, like limewire, or frostwire, nothing works and i am thinking of returning to windows! if someone can please help me out, i would greatly appreciate it.

---

### Post by Zimmer on 2007-01-16
> **Bullet666 said:**
> ok, i have tried every thing to get automatix to install. I have followed the directions on the automatix website, so i download the file, try and run it, but it won't open. It's the same with most programs i have tried to install, like limewire, or frostwire, nothing works and i am thinking of returning to windows! if someone can please help me out, i would greatly appreciate it.

[http://getautomatix.com/wiki/index.php?title=Installation#Installing_Automatix2_with_Apt](http://getautomatix.com/wiki/index.php?title=Installation#Installing_Automatix2_with_Apt)

Try using the apt method of installing Automatix.  (Make sure you use the instructions relevant to your installation of Ubuntu and processor..)

There is a lot of info about regarding how to use .deb files to install software, but using apt / synaptic is the 'easy' way and is what has made Ubuntu Linux easy to use IMHO   

Stick with it (Linux, that is )

ps** have you got gdebi  installed, as your original method , using the .deb file , will not install without it !!

---

