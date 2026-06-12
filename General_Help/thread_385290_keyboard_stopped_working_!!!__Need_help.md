---
title: "keyboard stopped working !!!  Need help"
date: 2007-03-15
forum: General Help
---

### Post by blunile on 2007-03-15
I was using opera browser on my kubuntu, when i clearly did something wrong by pressing shift / ctrl keys for seconds ... KDE showed me a message ..then suddenly my keyboard doesn't type any more ...

Restarting kubuntu doesn't help..   Can somebody help me ?????

---

### Post by blunile on 2007-03-15
well..No answer yet so i'll give little extra info :

the keyboard works on login, then once i get logged on it stop working completely !!
the mouse works fine ..

any ideas ??

---

### Post by blunile on 2007-03-16
Please people somebody help ??!!

I don't want to reinstall my kubuntu for 3rd time in a month.. every time something crashes like this with absolutely no reason  ??
Is the fact is kubuntu SUCKS ???  because i never saw an OS that suddenly decide to disable ur keyboard with no means to fix it !!!!!!

---

### Post by Mr. C. on 2007-03-16
Try Ctlr-Alt-2 and see if you get a login window. If so, log in, and type:

```
sudo /etc/init.d/gdm restart
```

If that fails, try Ctrl-Alt-Del to reboot.

MrC

---

### Post by steveM49 on 2007-03-18
Something similar happened to me yesterday.  I solved it by playing with the accessibility options.

My recollection was that by holding the shift and CNTL keys down, Kubuntu thought that I was requesting so called "slow keys".  Even without the keyboard, I was able to open the system settings then Accessibility, and shut down "slow keys".  The keyboard came back immediately.

As the saying goes -- "It's not a bug: it's a feature".

---

### Post by hikaricore on 2007-03-18
> **blunile said:**
> Is the fact is kubuntu SUCKS ???  because i never saw an OS that suddenly decide to disable ur keyboard with no means to fix it !!!!!!

Please slap yourself for me.

Never blame software for a user error.  These functions are put in place for a reason, if you fail to fully explore your new operating system and disable things you don't need, it's your own fault.

---

### Post by blunile on 2007-03-19
> Please slap yourself for me.

Never blame software for a user error. These functions are put in place for a reason, if you fail to fully explore your new operating system and disable things you don't need, it's your own fault.

Well I have to say you are absolutely wrong Hikaricore :) software are supposed to be fun to use and EASY.. You know what the word EASY means ???  I'm not dealing with a nuclear reactor were every mistake > kabooom .

and instead of blaming my ignorance y don't u make a suggestion to fix the problem ?? if in fact u know all the ''functions'' of your OS ??

---

### Post by blunile on 2007-03-19
Thank you .. thank you ,, thank you ..  sorry did i say thank you ?????

God bless you **steveM49** and thank you very much .. It worked like a charm for me ..

You are truly a friend and i appreciate ur help very much , I was on the edge of my seat trying to fix this ..  Thanx stevem49  :o

---

### Post by Mr. C. on 2007-03-19
> **steveM49 said:**
> ...that by holding the shift and CNTL keys down, Kubuntu thought that I was requesting so called "slow keys".  Even without the keyboard, I was able to open the system settings then Accessibility, and shut down "slow keys".  The keyboard came back immediately.

This is a good one to know.

[QUOTE=hikaricore]
Please slap yourself for me.

Never blame software for a user error. These functions are put in place for a reason, if you fail to fully explore your new operating system and disable things you don't need, it's your own fault.[/quote]
This is plain silly and a bit mean spirited.  Today's computer systems are so complex, it is not possible to "fully explore" the system.  Nobody does or can.  The features -  those that do present themselves - and their impact, are by no means always obvious or clear.  While functionality is "put in place for a reason", those reasons are only obvious to the designers (or lack there of).  The idea that holding down two keys such as Shift and Control should cause the keyboard to be unresponsive and provide no feedback is poor design.

MrC

---

### Post by hikaricore on 2007-03-20
> **blunile said:**
> Well I have to say you are absolutely wrong Hikaricore :) software are supposed to be fun to use and EASY.. You know what the word EASY means ???  I'm not dealing with a nuclear reactor were every mistake > kabooom .

and instead of blaming my ignorance y don't u make a suggestion to fix the problem ?? if in fact u know all the ''functions'' of your OS ??

I enjoy pushing people's buttons.  I won't even mention that I just made a bad pun in this very thread.

You handled the situation very well by not flaming back at me.  :)

On the topic of knowing all the functions of my OS?
I take a careful look at everything so I do know all of these functions, I even change/disable them to fit my own needs.

Anyway glad someone was able to help you, and in the future you'll find you avoid my types of responses when you don't spout crap like this:

> Is the fact is kubuntu SUCKS ??? because i never saw an OS that suddenly decide to disable ur keyboard with no means to fix it !!!!!!

You might not have meant what it seems like you did, but it's badly written and seemingly offensive to the community.

---

### Post by dajashby on 2008-01-29
This just happened to me, and I've spent a couple of hours trying to fix it.  IIn response to hikaricore, I would like to point out that the same thing can happen in Windows, except that Windows puts up a dialog box if it is about to invoke sticky keys, or whatever, and allows you to say no thanks Bill, I don't want that. linux just goes ahead and gaily stuffs you up with no warning. My problem started while running a VMWare session - I was shift-clicking a bunch of controls in a delphi project.  I am now going to see whether I can remove the accessibility features altogether...:)

---

### Post by grantek on 2008-02-22
Thank you all! :D

I experienced the same problem, caused by slowkeys - shortcuts for the accessibility features are now disabled .

---

### Post by kid-pro-quo on 2008-03-26
I realise this is an old topic,  I just thought I'd mention this isn't exclusive to kde/kubuntu for anyone searching the forums in the future.

To fix this in gnome, System > Preferences > Accessibility > Keyboard Accessibility.  Under the "Filters" tab un-check the "Enable Slow Keys" checkbox.

---

### Post by drewster1829 on 2008-06-27
> **hikaricore said:**
> I won't even mention that I just made a bad pun in this very thread.

You just did mention it, albeit indrectly.  Self referential statements may quickly become paradoxical.

> **hikaricore said:**
> 
On the topic of knowing all the functions of my OS?
I take a careful look at everything so I do know all of these functions, I even change/disable them to fit my own needs.

Wow, you know every option of every function of Ubuntu/Kubuntu?  You must have been one of the original developers for UNIX, in that case.  I'm really impressed. :o

Back to the original topic:  I'm glad I found this thread.  I accidentally enabled Slow Keys, and couldn't figure out what was wrong.  Thanks for whomever found the solution!  It *is* kinda silly to have it that easy to enable by default, IMO (with just a certain ctrl-alt combo held).  It would make more sense to have to enable the hotkeys in the Accessibility menu, unless a large percentage of Ubuntu/Kubuntu users actually use slow keys...:)

---

### Post by Mr. C. on 2008-06-28
> **hikaricore]I won't even mention that I just made a bad pun in this very thread.

[QUOTE=drewster1829 said:**
> You just did mention it, albeit indrectly.  Self referential statements may quickly become paradoxical.[/quote]

Such is an apophasis!

---

### Post by drewster1829 on 2008-06-29
> **Mr. C. said:**
> Such is an apophasis!

Now there's a 10 dollar word (maybe more, with monetary inflation today ;))!  I had to look it up, he he. :)

---

