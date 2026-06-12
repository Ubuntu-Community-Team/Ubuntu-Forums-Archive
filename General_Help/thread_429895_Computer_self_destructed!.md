---
title: "Computer self destructed!"
date: 2007-05-01
forum: General Help
---

### Post by Ozor Mox on 2007-05-01
So, I started up my Ubuntu laptop this evening thinking it was going to be the ordinary experience... how wrong I was.

It started up fine first time but it was being quirky. Network Manager would just sit and do nothing instead of trying to connect me to my wireless network. Normally it has to ask a few times, I think because of a weak signal, but it gets there eventually. This time, nothing. Trying to open up Places > Computer or Places > Desktop did absolutely nothing. So I went for a Ctrl-Alt-Backspace to solve the problem. Or maybe not. It gave me some message about the X server not starting because of an internal error. I can see all of my files from the command line, but startx fails. So I use halt from the command line to reboot.

This time fsck tells me that there's an error on the filesystem and it will check it. It gets to about 90% and fails, telling me to run it manually and all sorts of other weird errors like apt-get not being installed. Running startx tells me X isn't installed. Reboot into recovery mode. Same thing.

So I run fsck manually and get all sorts of errors for it to correct to do with missing inodes and weird stuff like that, which I have to press 'y' to each one (should be a yes to all option!) Then I reboot again using halt, which causes all sorts of weird things to happen including the system becoming completely unresponsive and listing the root directory's contents...I don't know what was going on. Eventually, halt ends services and powers down.

When the system starts back up, everything is completely back to normal. I will soon be making a backup and reinstalling Feisty (this was originally Dapper so that may not help).

What I'd like to know is...what the heck happened? Was this a hard drive corruption, did Ubuntu stuff up somewhere or did I stuff up somewhere? Fsck managed to do a pretty good job of recovering it, and everything is fine now, but something obviously went severely wrong.

Also, is halt a safe way to shut the computer down from the command line? I can't get any other commands to work. Shutdown -r or -h would say "waiting for timer" or something.

---

### Post by jimbob on 2007-05-01
[COLOR="Blue"]sudo shutdown -h now[/COLOR]  should kill everything immediately.

Don't know about your other problems.
&#65279;________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="2"]*Registered Linux User #400396*[/SIZE][/COLOR]

---

### Post by Ozor Mox on 2007-05-01
Thanks for that. Just to make sure I didn't corrupt anything with a forced shut down.

The other problems aren't really problems any more as it's working fine now, I just wondered if anyone could tell me why it happened. I suspect my hard drive got corrupted by something somehow.

---

### Post by ronacc on 2007-05-01
something may have gotten corrupted but I suspect your HD may be failing back up everything important right now,  if it is a failing drive it will get worse . if it was just a corrupted file and does not recur you will have a recent BU.

---

