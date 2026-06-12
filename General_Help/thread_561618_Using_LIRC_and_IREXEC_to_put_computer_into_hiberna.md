---
title: "Using LIRC and IREXEC to put computer into hibernate/suspend"
date: 2007-09-27
forum: General Help
---

### Post by efface on 2007-09-27
I have done some searching around and I can't really find a clear answer on how to get my computer to go into suspend or hibernate via remote.  I have LIRC up and working for my MythTV and I generally just leave the computer on.

My lady has recently gotten on me about that and wishes me to keep it off when not being used.  So now I am trying to find a way to hibernate/suspend the computer via remote and to turn it back on via remote as well.

Can someone please provide a link or the information itself?  I already understand what I need to add to .lircrc but as for the actually script for IREXEC to execute I have no clue.  I imagine the script would have to determine the computer state first and then execute wake or suspend based off that if I wish to only have to use one button.

Thanks in advance for your time.

---

### Post by pointone on 2007-09-27
1) Start the irexec daemon on boot; I do it via /etc/rc.local with the following command:
```
/usr/bin/irexec -d /path/to/.lircrc
```

2) Add the following in the specified .lircrc:
```
begin
    prog = irexec
    button = <HIBERNATE BUTTON>
    config = /etc/acpi/hibernate.sh
end

begin
    prog = irexec
    button = <SUSPEND BUTTON>
    config = /etc/acpi/sleep.sh
end

begin
    prog = irexec
    button = <RESUME BUTTON>
    config = /etc/acpi/resume.sh
end
```

Note, you can also use /etc/acpi/hibernatebtn.sh and /etc/acpi/sleepbtn.sh instead; test to see which one works better for you, although I assume it'll be the same.

Also note that I really doubt the resume button will work, since your computer probably won't see LIRC events while hibernating. For that, you'll need to check your BIOS settings for "wake on USB" or something like that.

---

### Post by efface on 2007-09-28
Thanks a bunch, I will give it a shot!

---

### Post by dominohc on 2007-09-30
I am having problems with my LIRC interacting with other programs besides MythTV.  I used this guide: [http://web.missouri.edu/~datcnc/leadtek_lirc_feisty.html](http://web.missouri.edu/~datcnc/leadtek_lirc_feisty.html)
to set up my remote and as I said, it works great with MythTV, but I can't seem to get my remote to work with tvtime or anything else for that matter.  I have the lircrc file in my /home directory and have created 2 test commands below the code for all my MythTV commands, neither of which work.  Here is my test code to try and get tvtime or rhythmbox to respond:
begin rhythmbox

begin
    prog = Rhythmbox
    button = ENTER
    config = play
end
end rhythmbox

begin tvtime
begin
    prog = irexec
    button = MUTE
    config = tvtime-command SLEEP
end
end tvtime

I can post all of my lircrc file if you think it will help.  Any ideas?  I have irexec running when trying to control tvtime and no reponse.  irw works fine and I can see my input, no problem and again, my remote works great with MythTV.  Anyways, just thought I would check.  Thanks for your help!

---

### Post by dominohc on 2007-09-30
After a couple hours of banging my head on the computer screen, I realized that the lircrc file needs to be in the home directory and named .lircrc (note the little dot)
I now have my remote working for mythtv and tvtime and feel comfortable enough that I can edit my file and add whatever programs I would like.  Just thought I would post what I was doing wrong in case someone else was as dumb as me.  Peace!

---

