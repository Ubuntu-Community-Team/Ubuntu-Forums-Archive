---
title: "Some bitter post-install comments"
date: 2005-10-20
forum: General Help
---

### Post by wahur on 2005-10-20
Installed Kubuntu Breezy on two machines: home desktop (fairly standard, year old) and G-Max laptop. The only peculiarity with install is that I left network unconfigured - I do not have broadband access at home, only very slow (19 kbs) dial-up.

**Initial impression** - nice eye-candy, sound works out of the box (none of the previous distros - Mandrake, Sarge, Hoary) could not achieve that. But this is where the good things end.

**Desktop**

1. If choosing Estonian language on installation, installer fails to set up user pw. It is known bug since Hoary. For gods sake, if you cannot support a language, please remove it.

2. Sudo was broken, cutting me out of ANY admin access to the box. See getbyhostname() bug widely discussed in these forums. Solved it using my Knoppix disk.

3. Sudo is STILL broken, with some admin functions (user management in System Settings and kcontrol) playing weird on me.

4. KPPP is broken, exiting with error code 1 immediately after dialing. Good god, kppp has been Just Working (TM) since I was recent Linux convert installing Red Hat 5.1 (or was it 6.something, dont remember anymore). 

5. OOo2.0 cannot create a Base. Or actually, base gets created but when I try to create a first table it just says something about not being able to connect to the database.

6. OOo2.0 cannot open big (15+Mb) .xls file. The same file opens just fine in OOo1.whatever in Hoary, as well as in OOo2.0 in Windows. Now this is major showstopper. And no, I will not send out 15 Megs of confidential data to sort out the bug.

**Laptop**

Bug 1 from desktop list applies here, too.

Sudo was broken, not letting me set up the network. Solved this with help from this forum, but again, some admin stuff still plays weird.

And guys. I have not even tried setting up printing, scanning, wifi, video and other usual troublemakers yet. I am still at the very basics!

Please. I am long past the phase where tinkering with distros and spending days in community forums was fun. I know darn well that ANY Linux install is bound to take SOME tweaking. But by now I would expect that certain basic stuff Just Works. I do not install or upgrade for eye-candy. And right now eye-and ear-candy seems to be the only part working well in Breezy.

---

### Post by petertc on 2005-10-20
5. OOo2.0 cannot create a Base. Or actually, base gets created but when I try to create a first table it just says something about not being able to connect to the database.

I think you need to install Java from Sun ( can't be shipped as Sun has it's own licence for this) 
This is the same with windows if Java is not on your machine then you cant use the database.

If i'm wrong then some one please let me know.

I must admit that i am very happy with the install on to my main PC i have been running Knoppix for the last couple of years and the install of 5.1 went with out a hitch and everything worked even the webcam. 

so at present i only have praise for 5.1 

Regards 

Peter

---

### Post by wahur on 2005-10-20
[QUOTE=petertc]I think you need to install Java from Sun ( can't be shipped as Sun has it's own licence for this)[/QUOTE]
OK, did not know this, and my Winbox has Java, thats true. Thank you for your info!

BTW, is there anything to do about a touchpad of the laptop that misbehaves - it sends wrong clicks all the time when in use so that, say, moving around a link-rich webpage or across some program interface with buttons becomes a major PITA. You simply must maneuver the mouse around any potentially active elements cos every icon and button and link seems to think I clicked it.

---

