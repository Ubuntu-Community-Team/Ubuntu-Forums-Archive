---
title: "What can be deleted from /var/? Any other privacy related things to delete?"
date: 2013-10-28
forum: General Help
---

### Post by markus.jansson on 2013-10-28
Im running a Lubuntu 13.04. I didnt get a good result from Google. I know that /var/log/ content can be deleted without any hassle and infact you might want to do that for privacy reasons. But what other stuff inside this /var/ directory can be deleted safely? By safely I mean that it doesnt crash my Lubuntu or cause any important settings to be erased etc. I dont care about loosing some debug info or something like that.

What other directories and files there are that you can safely delete for privacy reasons?

Im pretty new to Linux, so sorry for asking this kind of stupid question. I would know instantly what stuff to erase under Windows and there are also plenty of good programs for that in Windows. But on Linux, all I can see that do even some of that stuff is Bleachbit, but even that doesnt seem to do itse job perfectly. Ofcourse it would be perfect to get a program of some kind that would really erase (overwrite) everything that can be any privacy hassle, all logs and such...

---

### Post by buzzingrobot on 2013-10-28
What privacy concerns do you have about logs?  Do people you don't trust have access as  the root user on your machine?

---

### Post by Habitual on 2013-10-28
> **markus.jansson said:**
> I didnt get a good result from Google

Stuff in /var/ has nothing to do with Google rankings.
Unless your DocumentRoot is /var/log/ then there's little to worry about.

Please clarify this "result" you are referring to.

---

### Post by markus.jansson on 2013-10-29
> **buzzingrobot said:**
> What privacy concerns do you have about logs?  Do people you don't trust have access as  the root user on your machine?
If computer is seized, anyone can boot the computer from any media and bypass all filesystem/os restrictions. Normally, to counter this kind of attack I should ofcourse encrypt the entire hdd, but in this case that is not viable option, since there are cases where computer needs to be usable for limited user. Also, there might be cases where computer could be seized when its on, so encryption might not do any good. Its better to wipe all of these useless traces off my computer.

Logs tell great many things. I dont even know exactly how much in Linux, but much, that I do know. Also, there might be other files that I want deleted that can leak private information if computer is seized, one good example this is .thumbnail -directory, which keeps thumbnails of EVERY PICTURE I have viewed (fortunally Bleachbit can erase those easily).

---

### Post by buzzingrobot on 2013-10-29
> **markus.jansson said:**
> If computer is seized...


If you have a reason to be that concerned about seizure of your computer, logs might easily be the least of your problems.  We leave our traces all over the net, whether we use encryption or not. (And encryption is impractical for general use.)

As far as I'm concerned, the net is an open public arena, by design.  If I don't want something about myself exposed, I just don't put it out there, or on my PC.

---

### Post by markus.jansson on 2013-10-30
> **buzzingrobot said:**
> If you have a reason to be that concerned about seizure of your computer, logs might easily be the least of your problems.  We leave our traces all over the net, whether we use encryption or not. (And encryption is impractical for general use.)
This is not true, for example I routinely use anonymous VPN-services so that I dont leave traces to the net or to my isp unless I want to do so (just as writing this post with my real name). Anyway, that is not the point nor the question that Im seeking answer to.

My question still remains:
What files and/or directories you can safely delete from /var/ and are there other directories and files that you could safely delete in Lubuntu (that can give clues about what has been done with computer lately)?

---

### Post by buzzingrobot on 2013-10-30
The only way I'm know of to stop the generation of logs is to turn off the various loggers.  I don't know how to do that nor do I know what, if any, system impact it might have.

Setting up a log rotation scheme, to remove old logs to prevent their unending accumulation, is a commonplace Unix technique.

The other directories and their content in /var would, I suspect, either be recreated if removed, or their removal would break something. But, I dunno, because It's never occurred to me.

(You are much more trusting of techniques and services that promise privacy than I am. I don't think there's any foolproof way to protect my privacy online.)

---

### Post by philinux on 2013-10-30
/var/log needs to exist but files within it can be deleted.  The log system will nevertheless carry on creating new ones. 

I personally would leave things as they are. Unless there's a problem.

[http://askubuntu.com/questions/100004/how-can-i-free-space-from-a-massive-39-5gb-var-log-folder](http://askubuntu.com/questions/100004/how-can-i-free-space-from-a-massive-39-5gb-var-log-folder)

---

### Post by Lars Noodén on 2013-10-30
The main measure to take would be to encrypt your harddrive so that a passphrase is needed to use it.

Beyond that, traces of your activities are very, very unlikely to be found outside of /home and, specifically, your home directory.  Some browsers will support 'private' surfing where no history is kept and cookies are cleared upon clean exit of the program.  As to other programs, they keep their data in a variety of places inside your home directory.  If you look in your home directory for so-called hidden directories, you can go through what your programs are keeping yourself.  

```

ls -a /home/markus

```

Or if you are in Nautilus, you can press ctrl-h to toggle viewing of dot-files, it's also an option in one of the pull-down menus.  There should be some similar function in the other file managers if you are using something else.

---

