---
title: "synaptic installed fonts are listed but don't work at all"
date: 2007-06-22
forum: General Help
---

### Post by ikman on 2007-06-22
I Installed the ttf-gentium package on ubuntu Feisty last night with synaptic and, while I see the new fonts (Gentium and GentiumAlt) listed in the dropdown font list (in OpenOffice), they only type English characters, not Greek letters. After hours of web searching, I still haven't found the solution. It may have something to do with mapping? or X11?, but that's beyond my current expertise. Is there a simple fix for this problem?

so far I have tried these suggestions:

sudo apt-get install msttcorefonts
sudo fc-cache -fv
sudo apt-get install x-ttcidfont-conf
sudo dpkg-reconfigure locales

sudo fc-cache -fv ~/.fonts           [but I don't have a .font dir, only a .fontconfig dir, and there aren't any *.ttf files in that directory]


Thank you for your help,

---

### Post by Happy_Man on 2007-06-22
You have to make ~/.fonts yourself.

---

### Post by ikman on 2007-06-22
okay. I created the .font directory in my home, confirmed permissions of 644, then ran the fc-cache -fv ~/.fonts again. Then I searched .ttf and found where I think all the fonts are: /usr/share/fonts/... Then I went to ../ttf-gentium/ and found the four fonts  GenAI102.ttf, GenAR102.ttf, etc., and copied them to the new ~/.fonts dir and confirmed permissions 755. Then I re-ran the fc-cache command.

Then I rebooted the computer for the fun of it  (A Windows habit). I also checked "Applications->Accessories->Character Map" and both fonts were listed and "Greek" is listed as a Script, and the characters in the table look like the greek letters I want in my document. I just want to be able to type them from the keyboard and not have to copy and paste from the character map. 

But I still only get English letters when using the Gentium font.

I have used this font in both Windows and Fedora with great success. Is there a way to associate a certain keyboard layout with an individual font or something?

---

### Post by ikman on 2007-06-22
Well, I'm a little farther along... The solution has to do with SCIM and System -> Administration -> Language Support. 
Here are some additional commands that got SCIM to work using the hot-key toggle Ctl+Space (even though SCIM was  already installed by default):
sudo apt-get install scim-qtimm
sudo apt-getinstall im-switch
sudo im-switch -z -en_US -s scim

Then I did these:
1. System ->Administration -> Language Support and checked 'Greek, Modern' even though I really hoped to find 'Greek Ancient' or similar. Several language files were automatically installed.

2. System ->Preferences -> Keyboard [Layouts Tab] and added a layout called 'Greece Extended' 

3. rebooted

Now Ctl+Space toggles a taskbar SCIM with several language options listed, but Greek is still not listed there...

Can someone tell me what I must do to get Greek on that list?

Thank you.

---

### Post by ikman on 2007-06-23
Most of the above suggestions were unnecessary. Here is all you need to do: 

1. System -> Administration -> Language Support and add any languages you need. This may not even be necessary for keyboard mappings, but it didn't break anything. It will tell you that it is not completely installed and then downloads a few packages automatically.

2. (ttf-gentium is pre-installed with the operating system--nothing to do here)

3. System -> Preferences -> SCIM Input Method Setup and select languages you want (I think you are really selecting keyboard mappings for those languages). If the keyboard mapping you want isn't listed, type: 'sudo apt-get install scim-m17n'   This has the Greek (which I needed) and tons of other keyboards that aren't in the base install.

4. Control +Space toggles the taskbar SCIM manager on and off (At least until Ubuntu decided to create an icon that I had to click on to toggle the keyboard list on and off.) The keyboards work great now.

---

