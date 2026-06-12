---
title: "Text editor in Ubuntu makes DOS files?"
date: 2023-03-03
forum: General Help
---

### Post by stevermann on 2023-03-03
I am working on a shell script to automate some of my setup steps when I install Ubuntu on a new computer.
I generally write my scripts on my Windows PC using Notepad++.  It properly terminates my lines with LF.
When I "tweak" my script in the Ubuntu Text Editor, it adds \r, and the script won't run.

Question:
I recall seeing a macro that I could put at the top of the shell script to make it ignore \r, but I didn't write it down.  Does anyone recall this?
Alternately, is there a way to make the Ubuntu Text Editor save the files in Linux format?
Alternately-alternately, is there a better editor that I should be using?

---

### Post by DuckHook on 2023-03-03
Which flavour and version are you running? When asking for help, it is important to provide full info.

Assuming vanilla Ubuntu 22.04:

[LIST=1]
[*]Are you sure that the Ubuntu Text Editor (it's technically called gedit) is the culprit? As far as I know, gedit will never add the \r to any text file unless one installs a special plugin from the repos that does not come by default. Even then, you have to manually turn on the extension. Presumably, you would remember having done something like that.
[*]Other flavours install other text editors. But they are all similar in that they do not add \r. XFCE uses mousepad. You could try installing that and playing around with it.
[*]When working on scripts, I don't like gedit. I either work using CLI nano, or, if GUI, then geany.
[*]The real old&#8209;school types use VIM or EMACS. Too much machismo for me.
[*]However, in my opinion, it is far more likely that your Windows editor caused the problems. \r\n is just not a convention in Linux, but is the norm in Windows. I suggest the following: the next time you create a file in Windows, open it in gedit but don't modify it. Instead, use its *Find and Replace* function to find \r\n and replace with \n. If no results are returned, then the problem may indeed be with your gedit (still not sure how that could be). If a lot of results are returned, then the problem was already in the original file and it's not gedit's fault.
[/LIST]

---

### Post by TheFu on 2023-03-03
dos2unix and unix2dos are the normal tools.
vim has a mode that will let you set which end of line characters are used.

There isn't any single "Ubuntu Text Editor", there must be 50 of them.

Asking which editor you should use is like asking someone which religion or which flavor of ice cream is the best.  I'm walking away from the computer now, even though I have strong opinions on both those subjects.

---

### Post by stevermann on 2023-03-03
Thanks. I'll try Geany.  I don't know why I didn't use nano when I saw what was happening.  This is a script that I've used a few times before and when I saw an error like "can't open file \r", I knew what my problem was.

This is a new install of Ubuntu. I flashed *ubuntu-22.10-desktop-amd64.iso* to a thumb drive and let the install run as before.  I wanted to change one line in the script and since I was looking at it, a right-click then open in text editor.  It's the text editor installed from the .iso file.  I was surprised that it added \r to every line in the file.

Thanks for the geany tip.

---

### Post by DuckHook on 2023-03-03
Your new info about the version made all the difference. I recall reading somewhere that 22.10 dropped gedit in favour of something new. Yup, here it is: [https://www.omgubuntu.co.uk/2022/05/ubuntu-22-10-new-text-editor](https://www.omgubuntu.co.uk/2022/05/ubuntu-22-10-new-text-editor)
I'm not on Kinetic. No idea what they've changed. Try looking in the new editor's preferences to see if you can find a line end setting. It may not be obvious and could be something like "Linux behaviour" or "Windows behaviour". Alternatively, install gedit. It's tried & true and dependable.

---

### Post by DuckHook on 2023-03-03
Last but not least, do you really need a six&#8209;month hamster wheel release? If you have HW that won't work on Jammy, then you have no choice, but otherwise, a LTS release is more stable and better supported if for no other reason than the sheer numbers of users reporting on its bugs.

---

### Post by stevermann on 2023-03-03
> **DuckHook said:**
> Which flavour and version are you running? When asking for help, it is important to provide full info.

Assuming vanilla Ubuntu 22.04:

[LIST=1]
[*]Are you sure that the Ubuntu Text Editor
[/LIST]


[COLOR=#000000]This is a new install of Ubuntu. I flashed [/COLOR]*ubuntu-22.10-desktop-amd64.iso to a thumb drive and let the install run as before. I wanted to change one line in the script and since I was looking at it on the desktop, I did a right-click then open in text editor. It's the text editor installed from the .iso file. I was surprised that it added \r to every line in the file.*

---

### Post by TheFu on 2023-03-03
Geany is cross-platform, so you can put it on MacOS and MS-Windows, so you don't need to change editors with the OS.
Text-only editors are used by lots of people because we don't have any GUI on servers, but still need to edit files.

If you'd like to use Geany for editing system files too, just add this to your ~/.bashrc file ... top or bottom shouldn't matter:
```
export EDITOR=/usr/bin/geany
```
Next time you login, it will be the editor use by the **sudoedit** command which is a good habit to have. Takes a little to get used to that, but the added safety sudoedit provides is worth it.

I purge nano from all my systems as the 1st or 2nd command after install. I have no use for that terrible editor. If you are going to be scripting, you should really learn enough vi/vim to use it for simple tasks.  vim runs on all platforms - ALL OF THEM.  On routers, I've never seen any editor except vi.

I'm an LTS user too.  I might play with the 3 non-LTS releases, but they are toys in my mind. When an LTS gets released, I wait at least a few months before dipping into it for 1, low-risk, system. The last few months, I've been migrating my last 18.04 systems to newer releases.  

BTW, if you are seeking to automate system setup, can I point you towards ansible?  It is one of the tools that professionals use and is relatively easy to get started.  For example, I wanted to check which OS was running on all my systems, so I did an ansible command ... 
```
$ ansible -i hosts -a "lsb_release -d" cur |grep Descrip
Description:    Ubuntu 18.04.6 LTS
Description:    Ubuntu 22.04.2 LTS
Description:    Ubuntu 18.04.6 LTS
Description:    Ubuntu 18.04.6 LTS
Description:    Ubuntu 20.04.5 LTS
Description:    Ubuntu 16.04.7 LTS
Description:    Ubuntu 20.04.5 LTS
Description:    Debian GNU/Linux 11 (bullseye)
Description:    Debian GNU/Linux 11 (bullseye)
Description:    Ubuntu 20.04.5 LTS
Description:    Linux Mint 21.1

```
As you can see, I have some work remaining for 3 systems - 4 if we could the 16.04 box under ESM.  Handled 2 systems this week already. 

Ansible isn't perfect, but it is really handy for installing and configuring systems.  Nothing wrong with creating your own script either.  We did that for 20+ yrs before "devops" became something employers wanted in their buzzword list.  

Being consistent and constantly improving is the goal.  My 1st Five Minutes on a new system ... from a few years ago.
[https://blog.jdpfu.com/2014/02/28/1st-five-minutes-on-a-server](https://blog.jdpfu.com/2014/02/28/1st-five-minutes-on-a-server)  Anyways, hope the ideas in that link help.  My articles are about the "why" and I try not to include exactly what to type, since that is much harder to keep current.  Reviewing that article, there are many things I've improved in my desktop, server and linux container setups.  I worry about storage layout for physical servers now, but don't worry at all for containers.  Desktops get a slight amount of customization for storage, but not much more than using LVM with LVs for /, /home, /var, and swap.

---

### Post by Dennis N on 2023-03-03
Take a look at Notepad Next. It's described as a cross platform replacement of Notepad++
See screenshot
Available as a Flatpak

---

### Post by DuckHook on 2023-03-04
> **stevermann said:**
> [COLOR=#000000]This is a new install of Ubuntu. I flashed [/COLOR]*ubuntu-22.10-desktop-amd64.iso to a thumb drive and let the install run as before. I wanted to change one line in the script and since I was looking at it on the desktop, I did a right-click then open in text editor. It's the text editor installed from the .iso file. I was surprised that it added \r to every line in the file.*
Your thread motivated me to upgrade to Kinetic on one of my partitions. That upgrade has just finished flawlessly. I'm glad you prodded me to do so because I could now check that everything works—especially my LXD containers that I can now confirm to all work with Pipewire.

I was able to check out the new editor and the solution to your problem is simple:

When saving the file, select "Save As" then make sure you select "Unix Line End" at the bottom of the dialogue box. It offers you a choice of Unix/Linux, MacOS or Windows, so select the right OS and you should be fine. I suppose that selecting it once serves to set it as the default until you change it again. That would be the sane behaviour model, but you should probably test this a few times before relying on it.

I only toyed with the new editor for a minute before rebooting into this session to report back to you, so I'm going by memory, but it was dead simple. I like the look of the new editor and will be putting it through its paces in the next few days, but I trust that the above is enough to solve your problem for you.

---

### Post by stevermann on 2023-03-04
> **DuckHook said:**
> When saving the file, select "Save As" then make sure you select "Unix Line End" at the bottom of the dialogue box.

I didn't think of that. But, wouldn't you expect a Linux text editor installed in the latest Ubuntu image to default to "Unix Line End" in the first place?

Just a thought....

---

### Post by DuckHook on 2023-03-04
> **stevermann said:**
> I didn't think of that. But, wouldn't you expect a Linux text editor installed in the latest Ubuntu image to default to "Unix Line End" in the first place?

Just a thought....
Yes, I would generally agree.

However, Linux devs are also caught between the devil and the deep blue sea. For a long time, they have been relentlessly criticized for making Linux too hard for newcomers. This has made many projects choose to dumb down their offerings… eliminating options, setting Windows&#8209;friendly defaults, etc. I don't know how your text file was configured, but perhaps the new editor checks for some hidden Windows tag and then jumps to certain assumptions. I dunno. Just a wild guess.

My editor defaulted to "Unix Line End", so I don't know why yours didn't.

---

### Post by mIk3_08 on 2023-03-04
> **stevermann said:**
> 
Alternately, is there a way to make the Ubuntu Text Editor save the files in Linux format?
Alternately-alternately, is there a better editor that I should be using?
Mine, I usually use gnu nano or vim for the  Linux cli based editor. And I usually encounter this two when I have to  modify some script in Linux system. Regards and cheers.

---

