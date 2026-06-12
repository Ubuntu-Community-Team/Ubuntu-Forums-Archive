---
title: "Poor security by default?"
date: 2007-03-28
forum: General Help
---

### Post by risbac on 2007-03-28
There is something I need to clarify.

If you don't remember your password, you just have to reboot, choose "recovery mode", then type "passwd login" to change your password.

But what prevents ANYBODY to just change any password he would like? Am I missing something? Thanks in advance :)

---

### Post by spankymasterc on 2007-03-28
first of all why would anyone be using your computer and moving your settings?

And if someone is using your computer it prob someone u know and trust.....

Second of all if they do use your computer and its someone u dont know its probably someone who is not knowledge and doesn't know much about computer more less likely to know about ubuntu or any other operating system except Xp or vista.....:lolflag:

---

### Post by Catsworth on 2007-03-28
You're right.

Someone _could_ do that.

But.....

If someone has physical access to your box then it doesn't matter how 'secure' you think it is, they own it.....unless you've got some fairly serious hardware-level encryption on there, and all of your files are strongly encrypted, there's not one shred of information on there that they can't get to.

Your point about the much toted 'secure by default' is noted though, I guess it just depends on your definition of secure.

---

### Post by risbac on 2007-03-28
Yes, I agree with all this. But still, it just looks too easy... I know that a password on an account is not such a security; You can still access to all the files easily by mounting the harddrive on another computer. But I'm just surprised about how easy it is. In most cases it's not a problem, but I'm sure this could be a risk in some other cases. Am I paranoid?

---

### Post by theslut on 2007-03-28
no different to recovering the password on windows XP (although there are more hoops to jump through).

---

### Post by Tomosaur on 2007-03-28
If an attacker has physical access to a machine, there is absolutely no way of stopping them doing pretty much whatever they feel like. Security is generally designed to stop malicious code taking over your machine, and remote attackers from accessing your files. You simply cannot stop someone who is physically sitting at your computer from doing anything they like. It's not a Linux problem  you can do the same thing on Windows (Safe Mode), and probably OSX too, although I've never bothered to find out.

That being said, you can just remove the recovery option from GRUB, to at least put an extra barrier in the way. If the attacker knows how to fiddle with Grub via Grub's command line, then you're still screwed, although you can password protect Grub too. It's not really worth it though. If I was sitting at your machine and wanted to 'harm' you, I'd probably just take a mallet to the hard drive anyway. No password on earth is going to protect you from that :P

---

### Post by risbac on 2007-03-28
> If someone has physical access to your box then it doesn't matter how 'secure' you think it is, they own it

Ok, one example then:

a family shares a computer. Parents keep files in their account that they don't want their kids to have access to. Like websites with parental access. I cannot consider the kids as "intruders", they have access to the computer, but I don't see why they could so easily access to information from other accounts.

---

### Post by yopnono on 2007-03-28
> **risbac said:**
> Ok, one example then:

a family shares a computer. Parents keep files in their account that they don't want their kids to have access to. Like websites with parental access. I cannot consider the kids as "intruders", they have access to the computer, but I don't see why they could so easily access to information from other accounts.

I do agree, however set the password on the root account.

---

### Post by amac777 on 2007-03-28
How about this solution to make it harder for the kids to gain root access on a shared pc:

1. Change your BIOS settings so it boots from the hard disk drive first (not from a:, the cd, usb, or the network).
2. Add a password to your BIOS so no one else can change the settings
3. Set a default Grub selection (i.e., ubuntu), hide the grub menu, and make the default time for grub to 0 seconds.

Of course, they could easily beat this by shorting the jumper on motherboard to clear the bios password and then boot from a ubuntu live cd... or by taking out the harddrive...

So maybe add step 4 if you are *really* paranoid:

4. Pad lock the computer case so no one can open it.

Hope this helps!

---

### Post by Tomosaur on 2007-03-28
> **risbac said:**
> Ok, one example then:

a family shares a computer. Parents keep files in their account that they don't want their kids to have access to. Like websites with parental access. I cannot consider the kids as "intruders", they have access to the computer, but I don't see why they could so easily access to information from other accounts.

You can encrypt the files if you are that concerned - in which case there is yet another layer of defence. Regardless, it's a never ending circle. There is no such thing as bullet-proof protection when it comes to computers. If something can be locked away, it can be unlocked. If your kids figure out how to unencrypt stuff, then I'm afraid you're just going to have to accept it. The only 'really' reliable way of protecting your files is to store them remotely: ie on your work computer. There are probably websites which provide a similar service. You could also just email the stuff to yourself and have your email provider store them. Alternatively, just keep all of your sensitive/personal documents and files on a USB dongle which is in your possession at all times.

The end result, however, is that a machine is a machine. It will do what it's told to do, regardless of who tells it to do it. You can apply all the password protection you want, but it is always possible to crack this protection. This is not a Linux problem, it is the same on any operating system you will encounter. By all means, encrypt your hard drive. It makes no sense to have everything encrypted by default - most people are not so paranoid. Recovery mode is a useful feature to have, especially if something goes wrong with your machine, but if you don't want it, then simply remove it from Grub.

---

### Post by risbac on 2007-03-28
I totally agree with most answers. I don't have kids, it was just an example by the way ;)

But I think there is a big difference between cracking a password (requires to find the tools first, then to learn how to use it, etc.. etc...) and being able to change any password in a couple of seconds. It's just the easiness that surprises me a bit. I don't the security will never be perfect of course.

---

### Post by aysiu on 2007-03-28
[http://psychocats.net/ubuntu/security#recoveryrisk](http://psychocats.net/ubuntu/security#recoveryrisk)

---

### Post by tagra123 on 2007-03-28
> **risbac said:**
> Yes, I agree with all this. But still, it just looks too easy... I know that a password on an account is not such a security; You can still access to all the files easily by mounting the harddrive on another computer. But I'm just surprised about how easy it is. In most cases it's not a problem, but I'm sure this could be a risk in some other cases. Am I paranoid?

Most bios have settings that allow you to require a password to boot, but then as protected as that may seem it can be defeated by resetting the bios.

---

### Post by bazcor on 2007-03-28
[http://wiki.linuxquestions.org/wiki/Securing_GRUB](http://wiki.linuxquestions.org/wiki/Securing_GRUB)

---

### Post by thtrgremlin on 2007-10-28
This is not a flame, but I am a bit surprised by some of the suggestions here. I am a teacher and have Ubuntu on all but one of the machines running OSX. None of my students are Linux savy, but I would like them to be without them compromisingly the security of the machines. I also think there are several ways we can encourage student curiosity without creating barriers for those without overly curious ambitions.
1) bios boot password is annoying and creates a hoop for everybody unintentionally.
2) removing recovery mode makes administration a pain. While requiring techs to know how to boot to recovery mode wouldn't be much, and would clean up the menu (assuming a dual boot), it shouldn't be default lest the novice administrator.
3) hiddenmenu  / 0 timeout by default is too windowsish.I think that is self explanatory
4) locking out alternative boot devices in bios is good security practice, but nothing the ubuntu installer can (necessarly) take control of, or should for that matter.
5) locking out recovery mode and memtest by adding the "lock" argument and md5 encryption at the beginning of menu.lst encourages novice users in the right direction to what they should be doing, and pointing out to novice administrators that those options are for administrators.

"default" should be the best for everybody without being confusing or compromising. I think there should be some more effort in making ubuntu appropriate for functioning as a public terminal (library, K-12 computer lab). These will be a necessary feature for those applications, and something I need before putting my full effort into selling it to my school district. I have many other supporters, but this has been identified as a necessity, in part.

---

### Post by muralpennies on 2007-10-28
> **thtrgremlin said:**
> "default" should be the best for everybody without being confusing or compromising. I think there should be some more effort in making ubuntu appropriate for functioning as a public terminal (library, K-12 computer lab). These will be a necessary feature for those applications, and something I need before putting my full effort into selling it to my school district. I have many other supporters, but this has been identified as a necessity, in part.

Are you currently running LTSP thin clients or is each PC a complete Ubuntu install?

---

