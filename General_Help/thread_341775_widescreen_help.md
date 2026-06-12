---
title: "widescreen help"
date: 2007-01-19
forum: General Help
---

### Post by redsp1der on 2007-01-19
I recently formatted my main machine to reinstall WindowsXP and while I was at it I left a 25gb free partition so I could install Ubuntu.

First,  I installed 6.10 and everything went fine but I could not get it to display in the proper resolution or hz. I messed around trying things people have suggested here until I killed the OS (at least as far as I'm concerned).

So, I decided to try 6.06 because a few people mentioned their widescreen worked right off the bat or after updating with automatix2. I've tried envy, editing my xconfig or whatever file and automatix2. At least automatix  installed the nvidia control panel thing but there is still no option for 1440x900 60hz.

all so, now the OS choosing Grub thing is cluttered with an extra instance of Ubuntu 6.06 and its safe mode option.

my monitor is a 19" LG 194WT (1440X900 60hz) connected through DVI cable to a 6800 GT.

Please tell me I am doing something completely wrong and the answer is a just a few clicks away. I just booted back into Windows and thought Ubuntu had messed up my display settings for Windows untill I realized that I had been staring at the Ubuntu's skewed output for so long it was messing with my head.

---

### Post by der_joachim on 2007-01-19
Two suggestions:
1. put the following lines in your /etx/X11/xorg.conf, in your "Screen" section:
```

    SubSection     "Display"
        Depth       24
	Modes		"1440x900_60.00"
        ViewPort	0 0
    EndSubSection

```
This did the trick for me on my 20" monitor. Also: be sure that you have configured your monitor and video card correctly. You may have to calculate your own mode line. There is a nice command for it, but I cannot remember ATM. :oops: 

2. I use a Geforce FX5600. For some reason it refuses to play nice with my Samsung 20" monitor: with a DVI cable it will not go any bigger than 1280x1024. VGA works great though. Oh well. I will be buying a better card soon. If you can use your monitor and card with DVI in XP, this will not be a problem for you.

---

### Post by jimbob on 2007-01-19
Modeline generator is named gtf.   Enter this:

   gtf 1440 900 60

---

### Post by redsp1der on 2007-01-19
can you give me a step by step of how to do this. I don't  the command for editing my xorg.conf file. I tried to do it through the GUI but apparently I don't have permission to overwrite that file (WTF If I don't have permission then who does? I've already entered my password for this OS like 5billion times today).

I tried using xorg-edit but when I did a test it failed.

Why is setting up a monitor so difficult? I don't understand why it just doesn't recognize what the correct settings are.

---

### Post by Mithrilhall on 2007-01-19
```

sudo nano /etc/X11/xorg.conf

```

---

### Post by jimbob on 2007-01-19
Do you have the latest Nvidia drivers and the linux restricted modules installed?

From a terminal command line enter:

  sudo apt-get install linux-restricted-modules-$(uname -r)

  sudo apt-get install nvidia-glx
 
Unfortunately you are right, sometimes it can be difficult setting up a monitor but think of all you're learning.
&#65279;________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="2"]*Registered Linux User #400396*[/SIZE][/COLOR]

---

### Post by redsp1der on 2007-01-21
ok I'm still trying to set this up with no luck.

jimbob, I ran those commands and it said I was up to date.

Mithrilhall, thanks for the command I tired to edit xorg.conf per joachim's suggestion but I'm not sure I did it right. I added stuff but nothing seemed to happen.

what is this modeline? I ran gtf. Then what do I do? Do I copy that into xorg.conf somewhere?

---

### Post by jimbob on 2007-01-21
Is the native mode of your display 1440x900 according to the manual?

Try this for me:

Open a terminal window and type in su and then your password.
Enter the following commands (without the #'s):
#cd /etc/X11
#cp xorg.conf xorg.conf.save
#dpkg-reconfigure -phigh xserver-xorg
(you will be asked for card type - use up/down arrow keys to select nvidia.
use tab key to select OK, then hit enter.
you will be presented with a list of resolutions - use up/down arrows to select 1440x900.
hit the space bar once to select this resolution, it should put a splat (*) there.
hit tab to OK and enter.
 Now close everything and reboot to try the new xorg file.

Please post a copy of the new file (/etc/X11/xorg.conf) so I can look at it.
&#65279;________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="2"]*Registered Linux User #400396*[/SIZE][/COLOR]

---

### Post by grfd703 on 2007-01-21
I'm fairly new to Linux myself and I had a huge problem getting my monitor resolution to work in 6.06 or 6.10.  HOWEVER, I found the fix and it's rarely ever posted so I'm going to post it here.  

You have to MANUALLY edit your Xorg config file.  I'm at work at the moment and I don't have access to my "cheater" file where I keep the terminal command to manually edit the file, but once you get in, it's EASY.   Under the monitor section, Ubuntu improperly displays my monitor resolution as "1440x1440".  It SHOULD read "1440x900".  There are at least 5 instances of this in the Xorg config file that need to be changed.  Don't change anything else, just the instances of "1440x1440".  Backspace out the 2nd 1440 and replace it with 900 in every instance and save the file.  Close the terminal, and restart your computer.  The proper resolution won't yet be active and your screen might be a little messed up.  move your mouse curser to the top of the screen to shift it up if necessary.  Then go to "system" and "preferences" and select "screen resolution".  1440 x 900 should now be one of your choices among others previously not available.  I have to do this every time I reinstall or install on a different hard drive, but it does work.  

Could someone please post the terminal commands for backing up the Xorg config file and also for manually editing it?  Thanks !

Jim

---

### Post by jimbob on 2007-01-21
The commands have already been given above.

Get in the correct directory:  sudo cd /etc/X11

To copy:   sudo cp xorg.conf xorg.conf.save

To edit:    sudo nano xorg.conf

These to be done in a terminal window.  Notice that the window in nano will display the control commands for you at the bottom.

I use vi myself so cannot be of much help here.
&#65279;________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="2"]*Registered Linux User #400396*[/SIZE][/COLOR]

---

### Post by grfd703 on 2007-01-21
Ah.... there's why I didn't recognize the instructions above... you are using nano,  I am used to using gedit.  I think the command is "sudo gedit Xorg.conf" (or something like that).  Like I said, I'm at work and haven't memorized the commands yet.

---

### Post by Shatrat on 2007-01-21
> Get in the correct directory: sudo cd /etc/X11
You don't need administrator privileges to change working directory ](*,) 
Don't just put sudo in front of everything you type in command line, its not necessary and it can get you in hot water.

The only thing I had to do to get my widescreen monitor to work was edit the modes lines in the Screen section to include it.
Before:
 Modes      "1280x1024" "1024x768" "800x600" "640x480"
After:
 Modes      "1680x1050" "1280x1024" "1024x768" "800x600" "640x480"
For each color depth from 1-24.  Your mileage may vary but if you haven't done that, try it and then ctrl alt backspace to restart xorg.

---

### Post by jimbob on 2007-01-21
redsp1der:  I still think you should follow my procedure in post #8 above.

You have made a lot of changes and I'm not sure exactly what shape your current xorg.conf file is in right now.

This will give you a new clean xorg file to try and we can then go from there.

Please post a copy of the file when you get done.
&#65279;________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="2"]*Registered Linux User #400396*[/SIZE][/COLOR]

---

### Post by redsp1der on 2007-01-21
Ok it looks like its working now. in fact it looks wonderful.

It was grfd703's suggestion of replacing all the 1440x1440 entries with 1440x900. at first I didn't think it did anything because I just logged out but when I restarted the system I knew as soon as I hit the login screen somthing was different the text looked much crisper I guess becuase it was pushing the right hertz. Once in, I found 1440x900 on the list of rezes and all seems well.

Why is there a 1440x1440 entry in there, is it a typo or somehing? I've never heard of a square 1:1 monitor.

And why, after only changing the resolution entries, did it start using the right hertz? Before it was on the only option of 75hz. After the only option is 60hz; what it should have been all along.

BTW, jimbob, I tried your suggestion in post #8 but I couldn't get past the "su" part after I entered my password it would say,
"su: Authentication failure
Sorry."

Thanks for your time & help eveyone.

Now I just have to figure out how to fix my GRUB loader. Somehow, I got two instances of Ubuntu and the safe mode on the list (it doesn't seem to be causing any problems but it bothers me).

once again, thanks.

---

