---
title: "Taking a full screen shot of a website in console"
date: 2007-12-26
forum: General Help
---

### Post by self-defence on 2007-12-26
Hi,

I was wondering if there was a way for me to take a full screen shot (like the FireFox plug in ScreenGrab) of a website and save the image to disk in the console?

Thanks for any ideas on this. :)

Bye

---

### Post by wormser on 2007-12-26
You can press the Print Screen key, Applications> Accessories> Take Screenshot or this command gnome-screenshot --interactive and gnome-screenshot.

---

### Post by babil on 2007-12-26
**k-menu > Run Command > **[I][COLOR=Red]**ksnapshot**[/COLOR]
[/I]

---

### Post by self-defence on 2007-12-27
Hey,

thanks for the prompt reply but I guess I didn't express my self right.
Is there a way that I could take a snap shot of the full website not just the part that would be visible on the screen but do the this without a gui. Just in the command line.

Thanks again :)

Bye

---

### Post by p_quarles on 2007-12-27
I don't think it would be possible to create a tool like Screengrab that didn't rely upon an html rendering engine. There are several web browsers that will run in the shell (elinks, lynx, etc.), but I don't know of any tools for them that would do what you're looking for, and even if there were, these browsers don't render graphics all that well.

The closest thing I can think of would be a command-line download tool such as wget. You can use that to download the files that make up a web site, which in many cases would allow you to view the site offline with a graphical browser.

---

### Post by self-defence on 2007-12-27
Ok thanks for the information. That's what I thought.
So what you're saying is that in order to take a snap shot of a web site it needs to be displayed or rendered with rendering engine. Does it need to be displayed? Or could it be outputted to a file like an image? 
Any ideas on how I would go about or searching for something that would do the job or where I would start if I wanted to make something like that?

Well thanks for the help anyway. I thought that something like this was sure to exist.

Bye and thanks again.

---

### Post by self-defence on 2008-01-06
Well after searching I think I've found almost exactly what I'm looking for and I'm just posting back here to help anyone else that might need something similar.
It's called [Khtml2png]("http://khtml2png.sourceforge.net")(It can also be found in a deb package). It still needs an X server to take a snap shot of a web site, but as I understand it the x server doesn't need to bi in the same session as the command being run. I think.

Well thank you all for your help anyway. :)

Bye

---

### Post by SOULRiDER on 2008-01-06
Thats an interesting application. What i think is does is render the while page using Konqueror and then takes a screenshot.

The downside is that you need Konqueror meaning you'll need kdelibs which is a total bummer.

---

### Post by dlegend on 2008-01-06
I'm interested in this as well, though it'd be nice to see a gnome alternative using the gecko engine. It'd be a nice tool to have as a web developer =)

---

### Post by self-defence on 2008-01-06
Well as far as I know I don't have Konquerer installed but I do have a few things with kdelibs. But it works just as fine in Gnome. And since I don't actually need this tool with a GUI I think that I could just install X server and some of the libs needed in order for it to work. I hope the X server won't compromise the performance of the system too much. Maybe I could make a script that would start and stop the X server before and after needing this software and thus conserving resources but the down side of this is probably that this kind of procedure would again take up time witch would slow down the process and also use resources so I'll have to give it a try and see witch way is better.
But it's a nice peace of software and hat's off to the developer for taking the time and making it. Maybe someone else will find the time to make a version with the gecko rendering engine too.

Anyway a good night to all. :)

---

### Post by SOULRiDER on 2008-01-06
What computer are you using that doesnt run X? =/

---

### Post by self-defence on 2008-01-07
I was thinking of automating the whole thing and putting it on my server, witch in tern doesn't have X. But as I said I'll just install whatever I need. No biggie.

Bye

---

