---
title: "skype webcam problem, works in cheese, not skype"
date: 2013-01-13
forum: General Help
---

### Post by de Bacon on 2013-01-13
I have been dinking with this for a long time.  I found a resolution by following the instructions given by user TeoBigusGeekus link: [http://ubuntuforums.org/showthread.php?t=1937857&highlight=skype%2C+webcam+problem](http://ubuntuforums.org/showthread.php?t=1937857&highlight=skype%2C+webcam+problem)
Skype interfaces correctly with the web cam when using the command code: 
 LD_PRELOAD=/usr/lib/i386-linux-gnu/libv4l/v4l2convert.so skype

The problem with this solution is that skype is then tied to the terminal window.  It would be much more convenient to have the skype launcher open the program with this command where as it would not be tied to the terminal window.  

I tried editing the command in the edit function of its launcher replacing the command "skype %U" with "LD_PRELOAD=/usr/lib/i386-linux-gnu/libv4l/v4l2convert.so skype" but it doesn't work, gives an error to the command.  I am too ignorant about such things.

Can anyone help me finish resolving this issue?

---

### Post by sdowney717 on 2013-01-13
what version of skype?
4.1 works ok here just with nothing to configure on 12.04 64 bit

---

### Post by de Bacon on 2013-01-13
I'm using skype version 4.1.0.20
It doesn't work well for me here running the 32 bit version of UbuntuStudio 12.04 LTS

---

### Post by sdowney717 on 2013-01-13
on prior ubuntu versions, I had to do the ld preload vfl2 command.

Off hand, I wonder if you can upgrade to 64 bit or try on another hard drive running the 64 bit version.

You can boot a usb hard drive with 64bit OS or maybe try the liveusb 64bit. 

Or maybe someone will be able to make it work for you as is.

---

### Post by de Bacon on 2013-01-13
because of issues with my limited amount of memory (2 Gb) I have opted to use the 32 bit OS because it uses half the memory compared to a 64 bit system.  I could boot to an already loaded version of 64 bit, but that will not resolve the issue as I wish to use the 32 bit system vs the 64.

Edit, I forgot,  Thanks I do appreciate your effort to help

---

### Post by gandalf3 on 2013-01-13
i have had the same problem, going to the fix mentioned above.. thanks :)

> The problem with this solution is that skype is then tied to the  terminal window.  It would be much more convenient to have the skype  launcher open the program with this command where as it would not be  tied to the terminal window.  what do you mean by "tied"? does placing an & after the command work?

you could also make a custom launcher for it, it's fairly straight forward.. 
you could actually just edit the skype .desktop (in /usr/share/applications) and try changing the "Exec" value to the command you use to start skype. might be a good idea to keep a backup though.
hope this helps

---

### Post by de Bacon on 2013-01-13
> **gandalf3 said:**
> 

what do you mean by "tied"? does placing an & after the command work?

I mean, if I get skype running through the command line, then close the terminal window, both the terminal and skype close. 

Okay, I am trying to change the skype.desktop file, but I ran into permissions issues.  The problem I have with changing the permissions is I don't know the numeric value of the default permissions that I would like to switch back to.  If chmod 777 ..../skype.desktop  I don't know what the default permission equivelent to the numeric system that I use is.  In fact I wouldn't know were I to use the letter form of permissions either.  

As you may now understand, I know little of computing. 

Oh, placing the "?" at the end of the code didn't work either.  I tried it also with a space between the ? and the tail, to no avail.
Thanks

---

### Post by gandalf3 on 2013-01-14
you can change the permissions graphically in the properties.. (i do it that way, ;) it seems to work fine.)
i tried it, it works, but i needed to do a little work around, it didn't work with just replacing the line after "Exec".
i created a .txt file with the fix command in it, nothing else, then i made it executable by ticking the "allow executing file as program" box in the properties.

then in my edited skype.desktop, i made the "Exec" line a path to the .txt, and made sure the .desktop had "allow executing file as program" checked, and it worked :)
hope this works for you

EDIT:
my bad, for starting a program not tied to the terminal, you need parenthesis(spelling?) like this:
tied:
```
LD_PRELOAD=/usr/lib/i386-linux-gnu/libv4l/v4l2convert.so skype

```untied:
```
(LD_PRELOAD=/usr/lib/i386-linux-gnu/libv4l/v4l2convert.so skype
&)
```

---

### Post by de Bacon on 2013-01-15
Thanks for the help.  I didn't change the code in the skype.desktop file having a desire to fully understand how to change the permissions of the Owner, too lazy to switch to the root profile.  So putting that on hold was a favorable decision as since the video quality was so poor with that old webcam, I today got a new one that just works out of the box, no issues what so ever.  
Again thanks for the assistance.  I learned a bit in the process of this one.  Learning something is always better than not.  

Cheers :p

---

### Post by gandalf3 on 2013-01-16
glad you got things sorted out!
i have to thank you too, before i saw this thread my (unfortunately low quality) webcam didn&#8217;t work in skype..
now it does! :)
thanks.

---

