---
title: "Findings about PAM"
date: 2007-04-05
forum: General Help
---

### Post by maheshjagadeesan on 2007-04-05
I've been struggling to add my Ubuntu system (dual-boots with Windows XP Pro) to my company's Windows domain for quite some time now. I don't know whether my company uses an NT domain, a Win2k domain, an ADS domain, or whatever else it is. (I doubt it is an ADS domain, but I could be wrong) Of course, it goes without saying that on XP, my machine is happily part of the domain. So, I've been hunting the forums, Googling, doing everything I can to join my machine to the domain, but so far it's all been fruitless.

However, for the benefit of other souls who're in the same boat as myself, I'd like to at least share my learnings about PAM, Linux's pluggable authentication modules. This should be a series of posts, updated as I find out more. So, on to post number 1 :-)

(Btw, I've just installed the latest Feisty beta a couple of days ago, and everything seems okay)

In the folder /etc/pam.d, there are quite a few files, and one of them, **common-auth**, defines the authentication modules used by the entire OS. By default, the first uncommented line in this file should be
[INDENT]```
auth	required	pam_unix.so nullok_secure
```[/INDENT]
(let's call this line 1)

Now, after following some suggestions from [http://ubuntuforums.org/archive/index.php/t-91510.html]("http://ubuntuforums.org/archive/index.php/t-91510.html"), I added the following line
[INDENT]```
auth	sufficient	pam_winbind.so
```[/INDENT]
(let's call this line 2)
Immediately following this, I noticed that everytime I had to login to the OS, I had to enter my password twice. I think that's once per module. Also, on the same page above, there was a suggestion to change line 1 to 
[INDENT]```
auth required pam_unix.so nullok_secure use_first_pass
```[/INDENT]
(let's call it line 3)
Now, that turned out to be a screw-all suggestion, because on my system, that made all my login attempts futile! In other words, I couldn't login to the system at all.

Not giving up, I rebooted into the recovery mode, and played around with the settings until I finally figured out that line 3 was the culprit. Once I commented it out, and restored line 1, all was fine, though I still had to enter my password twice. Let me hasten to add that I'm calling line 3 a screw-all only after trying out all the suggestions on that URL above.

Before I close this post, let me make a request - if someone can give me step-by-step instructions for joining my machine to my Windows domain (along with instructions on how to find out the PDC for the domain), I'd be very, very grateful to him / her. 

Bye for now!

---

