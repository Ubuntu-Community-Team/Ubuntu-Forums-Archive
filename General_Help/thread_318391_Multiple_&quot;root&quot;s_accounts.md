---
title: "Multiple &quot;root&quot;s accounts?"
date: 2006-12-13
forum: General Help
---

### Post by telovoyagarcar on 2006-12-13
Whats the beef with the root account?

When i installed the SSH server, i read in the tutorials about password security stuff and decided to make the root's passwd stronger..
so i changed it with the "passwd root command"
So i got the "password changed suscessfully" or something alike message...

but... now i dont get it.
If i am in gnome, lets say i sudo a command and it will ask me for the password. but the new password does not work, but the old one instead...
So i thought that when you SUDO and then get the enter password prompt, you were being asked for the root's password... or when using synaptic, whatever...

Now my machine is screwed, ([http://ubuntuforums.org/showthread.php?t=318375](http://ubuntuforums.org/showthread.php?t=318375)) and i can't load gnome... but i get to the terminal, and i am being asked for the root password, and here, the new password is the one that works...

So are there root user for gnome, and a different root user for whatever you call the system outside of gnome?

---

### Post by ciscosurfer on 2006-12-13
When you *sudo* under your username, your asking the system to give you superuser rights for a temporary period of time.

The *root* *user* has its own password as well.  You don't need to use sudo with the root user, because the *root user is already superuser*.

Hope that made sense.

Here's some additional information for you: 
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)
[http://ubuntuforums.org/showthread.php?t=143461&highlight=visudo](http://ubuntuforums.org/showthread.php?t=143461&highlight=visudo)

---

### Post by cilynx on 2006-12-13
OK, you're confusing "root user" and "administrative access".

sudo gives you admin access if you're part of the admin group.  sudo wants your password, not the root password.

by default, ubuntu ships with root login disabled.  setting the root password allows you to directly log in as root.  it has no effect on sudo.

---

### Post by telovoyagarcar on 2006-12-13
I got it..
Thanks for the schooling!

---

### Post by hikaricore on 2006-12-13
You could do:

```
sudo -s
```

type in your old password, then at the root prompt type:

```
passwd
```

and type in your new password twice.

I've had this happen before where I couldn't login with the right password, but I could sudo with it, so I just did sudo -s and set the password again... and it worked.  >.<

Also if you're trying to login to GDM as root you need to enable it from another account via the login window or gdm preferences in the System/Administration menu.  Root access to X is disable by default for security purposes.

---

### Post by telovoyagarcar on 2006-12-13
Ohh.. about that security stuff..

I understand that the root account shouldn't be used because of security reasons... BUT

Why not just let this rule for the servers and "interesting honeypots" for the hackers?
I mean..
For a user like me.. that don't have anything really important in my desktop pc to attract hackers... and actually having to enter the damm password 38 times every 10 minutes because of reading this forum and learning new stuff all the time.. (configuration period), PLUS, having already a linux firewall with my internet connection (ipcop), what are the other "security" reasons that i should be concerned about to be avoiding the use of the root account??

I ask this because the keys i use in my keyboard to enter the password, are kinda wanting to retire and sue me because of the constant abuse!! LOL

---

### Post by cilynx on 2006-12-13
I think the idea is to make password storage a userspace setting.  If the root password actually exists, it's a system level setting leading to the various security issues discussed and debated at length everywhere.  If gnome is storing your sudo password, you still get the same effect from a user perspective, but without the "vulnerability" of having real root access. 

As an aside, I think disabling root login is really irritating, but it's nice to have the sudo log of all administrative activities.  Makes it easier to clean up after late night runs.  I leave it disabled on my Ubuntu boxen.  On my Debian boxen, I don't disable root login, but I have found that I generally log in as my user and use sudo as I "should".

---

### Post by tragicglee on 2006-12-14
> **telovoyagarcar said:**
> Ohh.. about that security stuff..

I understand that the root account shouldn't be used because of security reasons... BUT

Why not just let this rule for the servers and "interesting honeypots" for the hackers?
I mean..
For a user like me.. that don't have anything really important in my desktop pc to attract hackers... and actually having to enter the damm password 38 times every 10 minutes

 *Interesting* and *important* are *such* *relative* terms. I know that if I were the had the inclination and ability to gain access to your system AND run around as root, that would spark my interest, and I *would* poke around a while, though I wouldn't be malicious in my actions to any extent. I might edit your MOTD or something ("I was here but not I'm gone, and by the way, WHY is root logged on!?"). But there are people who would wreak havoc on your system if they could, either because they think it makes them 1337 or because they think some lessons are best learned the hard way! Its not even like they have to do something like delete a bunch of files and directories (and trust me, its amazing how quickly many of us realize just how *valuable* some "unimportant" data was when we realize that it's GONE) - they could access passwords to online banking and the like, they could set up a bot and use your computer to launch attacks, they could use your connection to download copyrighted material or kiddie porn to your hd and on and on and on.

I think that running as root is fine IF you're aware of the risks, prepared to accept them and know what you're doing, but a lot of linux newbies aren't and don't. I think that /having/ to sudo and enter a password cements the fact that certain things shouldn't be taken lightly, and makes people stop to think. I was talking to one of my ubergeek friends the other day, and he mentioned doing a "rm slash var hyphen Rf" while logged in as root in his newbie days. The root account on 'buntu can be unlocked, and I have no prob with people who want to do it, doing it,... but I'm against it being enabled by default. The best way to deal with bad habits is to curb them before they really get a chance to start. Linux is ever increasing in userbase and popularity, and I DREAD the day when 1 - people feel we're a group large enough to really warrant going after (in terms of viruses for the OS, security exploits, ect) AND there are a bunch of *completely clueless ninnies* logged in and running as root. IF it weren't so easy on Windows... ](*,) 

38 times in 10 mins? Are you prone to exaggerating, or are you just fond o' closing the term? I keep mine open and I'm asked once every 15 mins :p

---

### Post by bobosity on 2006-12-14
Well. That certainly was verbose.
Let's see if I can boil it down.

Even if your machine has no valuable information it can still perform a valuable service. It can allow me access to other computers while disguised as you. This is a bad thing.

If some rogue program wants power user status, it has to ask for your permission. This is a good thing. Unless, of course, you are already running as root. That is a bad thing.

If, after running sudo, you leave the terminal open, the program will remember your password for a while.

---

