---
title: "Keymap problem i Feisty - Swedish keyboard"
date: 2007-05-08
forum: General Help
---

### Post by james.wilde on 2007-05-08
I upgraded to Feisty about a week or so ago, both on my workbox and my laptop.  Now the keymapping is broken.

When I connected to my workbox over vpn from a Windows machine at home, I could not enter the symbols represented by Alt-Gr plus another key, for example Alt-Gr+2 gives @, Alt-Gr+7 gives { and so on.  I solved the problem (shortage of time) by having an alias on the workbox which wrote the symbols to a terminal window and copied and pasted, a real pita.  When I installed Ubuntu also on the home machine, the two could communicate with each other directly.

Now, since upgrading at work and home, my Ubuntubox at home has the same problem as the  Windowsbox - I cannot write the Alt-Gr characters without cut and paste.  I have been looking for some kind of keymap file (I'm brought up on Solaris) that I can modify, but haven't found anything yet.

Any idea where I may be able to find this or suggestions for other solutions?  Naturally I have the standard Swedish keyboard specified on both boxes, but the locale is en_US.

TIA

//James

---

### Post by Icebear on 2007-05-08
go to >system>preferences>keyboard>layout options>third level choosers

then select what key you want for the third group

 which when you press with say for example "key 2" should give you @

in the Swedish keyboard

---

### Post by james.wilde on 2007-05-08
Good try, Icebear, but no cigar!

I have that setting on both the homebox and workbox, but I still can't enter Alt-Gr+2 on the homebox and get the @ sign on the workbox.

//James

---

### Post by Icebear on 2007-05-09
mmmmmm

Have you set the 3rd key lever maybe try another key. I use the window key.

---

### Post by james.wilde on 2007-05-09
Thanks, tried that, too.  What presumably is happening is that the Alt-Gr+2 combination is generating @ on the local machine, but for some reason this is not being sent - or received - properly over the vpn link, as it was before with Edgy,

Unfortunately I don't really have the competence to explore the problem and find out why, and how to fix it.

//James

---

### Post by james.wilde on 2007-08-30
Still got this problem.  Any suggestions on how I might be able to research it?  Is there some program I can install to test what key code is being sent by the transmitting machine, which can be either Windows XP or Feisty,  when I press, say, Alt-Gr+2 (@) or Alt-Gr+4 ($) and, more importantly, what is being received by the remote machine?  Maybe then I can try some key mapping on the remote machine when I am working at a distance.

I have discovered that, not only do I have a problem with the third symbol on a key, but also with the key to the left of 'z', which has < (lower case) > (higher case) and | (Alt-Gr).  I get an x instead of < and > and nothing for |.

Very grateful for any pointers.

//James

---

### Post by parasl on 2007-11-13
Hi,

I got a similiar problem that I can figure out what's happening. 

When I ssh on to my ubuntu-machine at home I can't get åäöÅÄÖ to work, I just get rubbish letters on the prompt. What I use is putty on a windows machine, but that one hasn't been changed in ages.

So I thought it would be a locales-problem and I regenerated them and reconfigured locales and that went smooth but still rubbish letters. any ideas?

This was working before upgrade to 7.10.

---

