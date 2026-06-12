---
title: "Root File System Full"
date: 2024-07-21
forum: General Help
---

### Post by charmingfox2976 on 2024-07-21
I have had a message that my 'root filesystem is full'. At the moment I Cannot install new and updates. Please view the terminal screen image enclosed via attachment.[IMG]https://ubuntuforums.org/attachment.php?attachmentid=294000&stc=1[/IMG]

---

### Post by #&amp;thj^% on 2024-07-21
Try this first:
```
sudo apt autoremove
```
Then run your update and upgrade command again.

---

### Post by Rubi1200 on 2024-07-21
I would also recommend running this:

```
sudo apt clean
```

If neither of the commands we suggest solve it, then please post the output of this command:
```
df -hT -x squashfs -x tmpfs -x devtmpfs
```

---

### Post by #&amp;thj^% on 2024-07-21
Nice addition Rubi1200, I failed to read the bottom line For /var/cache/apt/archives/ :)

---

### Post by yancek on 2024-07-21
One way that a system can get full is with excessive log files so you might check to see if you have particularly large log files.  If you have been experimenting and getting a lot of errors this would be a good place to look.

```
du -h /var/log
 
```

---

### Post by charmingfox2976 on 2024-07-23
Both apt autoremove and clean didn't work. Please find a copy of the terminal output enclosed via attachment after I inputted the two commands you have suggested.

---

### Post by oldfred on 2024-07-23
Please do not post screen shots unless gui and then only as attachments. Hard to read especially for older eyes.

Easy to add code tags around text or terminal output with Forum's Go Advanced editor and # icon.
Code Tags
[https://ubuntuforums.org/showthread.php?t=2497846](https://ubuntuforums.org/showthread.php?t=2497846)
I sometimes use the quote icon in quick reply and just edit quote to code.
If using Quick Reply then[noparse] ```
 at the beginning and 
``` at the end. [/noparse]

If you use the Forum's Go advanced editor, you can use the paperclip icon to attach screenshots or other info. Post #4 , also no larger than1024x768 if photo
[https://ubuntuforums.org/showthread.php?t=2054969&p=12229098#post12229098](https://ubuntuforums.org/showthread.php?t=2054969&p=12229098#post12229098)

I like to use ncdu starting at / to find large folders & files. Saves running multiple du commands.
sudo apt install ncdu
cd /
sudo ncdu
arrow, enter & q keys to move about

---

### Post by charmingfox2976 on 2024-07-25
ncdu 1.15.1 ~ Use the arrow keys to navigate, press ? for help                                                                                                                                              
--- /home/user ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  185.3 GiB [##########] /.local                                                                                                                                                                            
   30.0 GiB [#         ] /.var
   11.5 GiB [          ] /.cache
    5.2 GiB [          ] /Pictures
    2.8 GiB [          ] /.config
    2.1 GiB [          ] /Downloads
  321.4 MiB [          ] /snap
   56.6 MiB [          ] /Videos
   17.8 MiB [          ] /.thunderbird
    2.0 MiB [          ] /VirtualBox VMs
  348.0 KiB [          ] /.snap
   76.0 KiB [          ] /.pki
   56.0 KiB [          ] /.nv
   52.0 KiB [          ] /Snap
   52.0 KiB [          ] /Documents
   44.0 KiB [          ] /.gnupg
   16.0 KiB [          ]  .bash_history
   12.0 KiB [          ] /.android
    8.0 KiB [          ] /.mozilla
    8.0 KiB [          ]  .fedora36-wor-2.draft.txt
e   4.0 KiB [          ] /user-Aspire-A517-52G
e   4.0 KiB [          ] /Templates
e   4.0 KiB [          ] /Public
e   4.0 KiB [          ] /Music
e   4.0 KiB [          ] /Desktop
e   4.0 KiB [          ] /.ssh
    4.0 KiB [          ]  .bashrc
    4.0 KiB [          ]  .xdp-PGP Private Key.asc.nIWQiU-pmIJZ9
    4.0 KiB [          ]  .viminfo
    4.0 KiB [          ]  .profile
    4.0 KiB [          ]  .bash_logout
    0.0   B [          ]  .sudo_as_admin_successful
[IMG]https://ubuntuforums.org/attachment.php?attachmentid=294014&stc=1[/IMG]

---

### Post by #&amp;thj^% on 2024-07-25
You really need to use code tags, most of us will just ignore until you do that. oldfred has showed a few ways to do that.
Did you peek inside of:
```
185.3 GiB [##########] /.local
30.0 GiB [# ] /.var
11.5 GiB [ ] /.cache
2.8 GiB [ ] /.config
```
I would first look there to see if anything there can be moved(To a back-up Drive) or just deleted.

---

### Post by deadflowr on 2024-07-25
Should be able to clear the .cache right now without any need to investigate.

.var seems really big, it's usually the flatpak directory in your home folder, really. But that's massive, like you have 100s of flatpak apps installed or something.
or have flatpak apps that are saving data to the wrong location.

.local might be the trash folder, look in .local/share/Trash. Could be you've only moved to Trash but have not emptied it yet.

---

### Post by #&amp;thj^% on 2024-07-25
> **deadflowr said:**
> Should be able to clear the .cache right now without any need to investigate.

..
I don't disagree with that but,  If your .cache is growing large, it might be better to look at the contents and determine what application is making it large and re-configure a bad acting application (rather than simply deleting .cache when it grows too large).
EDIT:
This will list only whats there:
```
find ~/.cache/ -depth -type f -atime +365 
```
This will delete them:
```
find ~/.cache/ -type f -atime +365 -delete

```

---

### Post by deadflowr on 2024-07-25
Yeah, investigate is probably the wrong term here.
What I meant is you don't have to dig through the files to see what to keep and what not to keep.
It's all junk more or less.

---

