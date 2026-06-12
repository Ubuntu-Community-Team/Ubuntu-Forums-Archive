---
title: "I need help with final 5%, Don't make me use windows"
date: 2005-05-07
forum: General Help
---

### Post by SuperKev on 2005-05-07
Ok,

I've been using Ubuntu for about two weeks now, I started with Kbuntu but it was very buggy for me so I switched to Ubuntu and now can at least do the basics like internet and email BUT...There are some annoyances/bugs that are keeping me from fully enjoying and being productive while using Ubuntu/Linux. So I either need to get these things sorted or I am going to be forced to return to using Windows, which is something I don't want to do but I need to be able to do my work if I am going to be able to fully convert to Linux. Since my problems are varied I didn't know exactly which forum to put this in so I hope you don't mind. So before I either just quit using Linux or switch to another distro maybe some of you can help me out. And yes, I have read the wiki, and all other sources of information I can find before posting this, so this is a last ditch effort to get Ubuntu configured the way I need to before simplt running out of time and moving on. Below is a list of my particular issues and follwed by my system specs, thanks to all in advance.


1. (and particularly annoying) When typing , especially on message boards I suffer from outrageous lag from my keyboard inputs, in fact I am having to deal with it at this very moment, I will type some sentences and when I look up I have to wait sometimes several seconds for the text to appear, which slows me down to an unacceptable rate when typing and makes it very difficult to correct mistakes as I have to wait to see all the text and then go back.

2. Copy and paste commands for root terminal from the wiki or ubuntuguide.org never has worked as I cannot copy/paste them and uncomment them before they seem to run and just give me an error message, even when I do manage to uncomment them I usually get 'command not found'.

3. I need to install universe and multi-universe repros but cannot seem to do it (see above)

4. On certain websites I cannot access enlargement of pictures or conversely links posted by others the cursor doesen't seem to see them so I cannot click the link to see the content or what is linked to.

5. Sound- I have none. Have tried all the 'tips and tricks' I have found documneted but nothing has worked and anything I try to do from the CLI is mostly futile. Sound card works when I boot into Win2000pro so I know it's not a hardware issue. Card is a Yamaha OPL3-SAx sound card. Probably very old I know but this is my spare PC.

6. And last, I have my main WinXP computer and this one both running through a router, I need to be able to access files on my Windows machine , word docs for example, edit or modify them and then either save or print them. I have heard about SAMBA but all the tutorials I have found are in such geek speak as to be useless to a n00b like me.

I really like Linux and I installed Ubuntu at the advice of a couple of friends who are long time Linux users, and I want to keep using Linux and Ubuntu in particular BUT, it's getting to a point that the bugs and time and effort to correct them is a diminishing return. Please forgive the laundry list of my issues and the typos, the lag is very bad right now, any help will be truly apprciated and gratefully acknowledged.

System Specs:

AMD K6-2 400mhz CPU

192 MB PC100 RAM

Yamaha OPL3-SAx Sound card

Nvidia GF2 MX 400 GFX Card 64 MB

Dual Boot Ubuntu Hoary/ Win2000pro SP4

Thanks!!!!

---

### Post by nad on 2005-05-07
I'm sorry that you are having issues. Your persistence is admirable and as you understand that any new tool involves learning how to use it you will find that the rewards are great.

The keyboard problem is likely bios related. Adjust the typematic rate and test.

Copy and paste is often not necessary as any text highlighted is automatically in the clipboard buffer. Simply highlight, move to your input window and middle click. Click timing and motion are usually the culprits. They take some getting used to. I sometimes find myself with the same errors you have encountered. Some program user interfaces however will require that you explicitly copy to the clipboard.

Speaking of user interfaces, synaptic leaves something to be desired. You have to enable the 'Show Disabled Repositories' in order to be able to select them. Talk about counter-intuitive!

Firefox and internet exploder both use proprietary extensions. A website that is not coded for all browsers will seem deficient to some. For a fully w3c compliant browser that attempts to correctly display all content, try opera.

Sound has been a hoary issue from the get go. I will not go into it.

As far as sharing files is concerned, ubuntu has been locked down tight. Getting networking properly configured is a source of pride for any geek. As you now have a secure network, it is time to become your own system administrator. Doing it the right way has advantages and takes a fair amount of knowledge. Getting either samba or nfs configured to your requirements is your challenge. There is a wealth of information out there. A large percentage of all web documents is related to networking. You may wish to start at [www.tldp.org](www.tldp.org) for your base research, as well as some ubuntu specific howtos here.

Please keep us posted. The community is here to help.

---

### Post by kamstrup on 2005-05-07
Ok. I will give it a shot then ;P Mind that I need more info to give conclusive answers to most things.

Firstly your system specs are really the absolute minimum I'd consider running Ubuntu on. Actually I'd probably go for 500Mhz/256MB as a bare minimum. Furthermore old hardware tend to be problematic generally. Using newer hardware solves *many* issues.

1) "When typing..." Do you mean that this behavior shows in all applications (OpenOffice, Gedit, Gaim etc.)?  This is really weird, I must say.Are you using a ps/2 keyboard or one of the older ones (can't remember what they're called)?

2) Many problems from copy-pasting into terminals arise from the newlines inserted by your browser. Make sure that the commands are pasted as one long line.

3) It sounds like you are trying to configure multi-/universe by editing the /etc/apt/sources.list... I don't know why so many people do this. It is much easier to just click System->Admin.->Update Manag. click Preferences and then add it...

4) Are you sure those images are links? I've never heard of this before. If Firefox is giving you headaches, you might try installing Epiphany. It seems a bit lighter to me.

5) Again. Old hardware = headache... :-S Sorry, I'm of no help here.

6) Samba. Sorry again. I no *very* little about this.

Suggestion: Since you computer is not an all-out-man-eating-number-crunching-bitspitter you might consider installing the XFCE4 desktop environment instead of Gnome. Just install the xfce4 package from universe.

Cheers!

---

### Post by rdsmith1 on 2005-05-07
if you dump your xp files into a shared folder when you look at the network in ubuntu you should be able to see and copy those files. Are you using kde or gnome ?

---

### Post by SuperKev on 2005-05-07
[QUOTE=rdsmith1]if you dump your xp files into a shared folder when you look at the network in ubuntu you should be able to see and copy those files. Are you using kde or gnome ?[/QUOTE]

Gnome. I'd like to be able to try fluxbox but haven't been able to figure that out yet and I'm afraid to install KDE although I like it and there seems to be a greater amount of themes for it. I tried installing a Gnome theme but stuffed it up. 

I DL'd Epiphany browser and that seems to have sorted the keyboard lag issue, although I wish it had some of the features for tabbed browsing as firefox does. I might try Galeon too just for comparision. 

Would I need samba for file and printer sharing? 


Thanks for all the help so far, I feel better about sticking with Linux/Ubuntu as things get sorted one by one,

---

### Post by SuperKev on 2005-05-07
[QUOTE=rdsmith1]if you dump your xp files into a shared folder when you look at the network in ubuntu you should be able to see and copy those files. Are you using kde or gnome ?[/QUOTE]

Gnome. I'd like to be able to try fluxbox but haven't been able to figure that out yet and I'm afraid to install KDE although I like it and there seems to be a greater amount of themes for it. I tried installing a Gnome theme but stuffed it up. 

I DL'd Epiphany browser and that seems to have sorted the keyboard lag issue, although I wish it had some of the features for tabbed browsing as firefox does. I might try Galeon too just for comparision. 

Would I need samba for file and printer sharing? 


Thanks for all the help so far, I feel better about sticking with Linux/Ubuntu as things get sorted one by one,

---

### Post by kamstrup on 2005-05-08
I would try XFCE4 before I'd go for fluxbox. Fluxbox is slick and *really* lightweight. Xfce4 still gives you eye-candy while being relatively light on system resource usage. Just install xfce4 from synaptic.

What's wrong with the tabs in Epiphany? They run fine for me... 

Cheers!

---

### Post by SuperKev on 2005-05-08
Well,

Got it mostly sorted except for file sharing and printing now. I tried Epiphany, Galeon and somehow regular old Mozilla got installed too. I uninstalled firefox bit for some reason that required me to uninstall epiphany too, but I firgured I didn't need 4 browsers. I am going use Mozilla and Galeon for a while and see how that goes. Apparently the keyboard lag issue was related to FF, since I don't get it in any of the others. 

Ok, on to trying to figure out file and printer sharing. Samba?? Something else??

Skol

---

### Post by graigsmith on 2005-05-09
im trying to get file sharing up and running too.  between my ubuntu box, and a win 98 machine.  do i need to download Samba or no?..  when i click on the windows networking icon.  it opens up a window smb:///  and it shows nothing.  if i make a connection to smb://192.168.1.112  then i can see the directory shared on the win 98 machine.  the win 98 machine can't see the shares on the linux box though.  im not sure how to fix this.

---

