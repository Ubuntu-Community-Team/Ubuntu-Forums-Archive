---
title: "Help with two bugs"
date: 2014-08-20
forum: General Help
---

### Post by nop2 on 2014-08-20
Let's see if someone can help me with two mini-bugs I have: 

  
[LIST]
[*]Sometimes, when I close the laptop and later open it, the  touchpad stops working properly. Most times it only acts fuzzy a few  seconds and then starts working fine, but other times it stops working  completely (I can't move the mouse arrow, althougt clicking buttons work  fine) until I restart.

[*]Whenever I turn on the computer, some keys excange with others ("  becomes @, ? becomes _, ¿ becomes +, etc), and I have to go to Keyboard  input and add and delete some language (I use Afgan because it's the  first)
[/LIST]
  Thanks.

---

### Post by T.J. on 2014-08-21
The first sounds like your sleep/resume is not working properly.  This could be a bad driver or a really crappy install - not your fault - Ubuntu does some things rather strangely.  As for helping you fix it, I don't have enough information. =(  I'd need the laptop model, and specifically what software and versions you are using.  As a short term fix in the meantime, you can always turn off sleep mode and shut the laptop off when you are not using it.  Linux does not take that long to restart.

The second sounds like your keymap is not set properly.  Are you a native English speaker or work internationally?

---

### Post by nop2 on 2014-08-22
I have an Asus F551CA-SX079H. I wiped the hard drive (it came with Virus 8) and installed Ubuntu 14.04. Now that you mention it, one of the first times I closed the computer it said something about a sleep bug (it only happend once, so I don't remember it well). But, I have disabled sleep on close, so it (should) only turn of the screen.

Yes, it seems that's someting about keymap. I have a Spanish keyboard, but it seems that when I restart the keymap resets to English (that's why adding and deleting a language fixes it)

---

### Post by T.J. on 2014-08-25
I'm programming on the torture of Windows 7 this week so I'm sorry I can't list the file names or test things presently.

Have you checked the localisation files under /etc to make sure the default languages are set to your preferences?  It sounds like Ubuntu is remapping them every time that you start X.   There are a number of files under /etc: vconsole, locales, etc that control the keyboard layout.  You should be able to find plenty of specific references online.

Have you tried "sudo setxkbmap -layout us" or whatever layout you prefer rather than US?

---

### Post by nop2 on 2014-08-27
sudo setxkbmap -layout es works the same as adding an deleting a language in keyboard input: corrects the keboard layout but after restarting it resets again.

---

### Post by T.J. on 2014-09-16
Since this is Ubuntu have you tried setting the keyboard in Unity?

---

