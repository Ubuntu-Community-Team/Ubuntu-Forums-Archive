---
title: "Natural Scrolling in 12.04"
date: 2013-07-04
forum: General Help
---

### Post by sliberty on 2013-07-04
I have installed Crouton (Ubuntu 12.04) on my Chromebook. As a Mac user, I am used to Natural Scrolling, and was able to configure the ChromeOS to scroll that way as well. But when I installed Crouton, there didn't appear to be a way for me to set it up for the Linux side of my Chromebook.

Then I found a web page that told me to do enter this in a terminal session:

[COLOR=#000000][FONT=monospace]echo "pointer = 1 2 3 5 4 7 6 8 9 10 11 12" > ~/.Xmodmap && xmodmap ~/.Xmodmap

And it worked, sort of. The next time I started up Crouton, scrolling was back to the old way.

Perhaps it is because I cannot do a graceful shutdown of Crouton. Maybe this change was not really saved properly. Or maybe something else is at work. 

Anyway I am open to all suggestions for a way to permanently enable Natural Scrolling.

I am not an expert on Ubuntu by any means, so a little explanation (so that I can learn) would also be appreciated.

Thanks,
Steve

[/FONT][/COLOR]

---

### Post by awo3 on 2013-12-25
Have a look at [this]("https://wiki.archlinux.org/index.php/Xmodmap#Reverse_Scrolling") for some information on xmodmap and specifically the command you are using. Your command creates a new file called .Xmodmap in your home directory with the contents [COLOR=#000000][FONT=monospace]

pointer = 1 2 3 5 4 7 6 8 9 10 11 12[/FONT][/COLOR]

You next tell the terminal to pass the file you just created to the command xmodmap (upon successful completion of the first command, that's what the && means). After you restart your computer, the file remains, but xmodmap has not loaded your custom changes into Xorg because they are not the default settings. To ensure that this happens everytime you restart your computer, go to the .bashrc file located in your home directory. This file contains commands that are ran everytime you login. Simply add xmodmap ~/.Xmodmap somewhere in the .bashrc file and you should be good to go.

Andy.

---

