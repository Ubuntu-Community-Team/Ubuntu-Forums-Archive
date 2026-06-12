---
title: "Experienced Linux users : do you automate ?"
date: 2008-05-05
forum: General Help
---

### Post by Andre-D on 2008-05-05
Hi.
how do I automate GUI actions in Linux ?

Like: I'd like to press some button combination, then the mouse should move to a specific location in FireFox, press mouse button, select an area by dragging, release the mouse button, simulate Ctrl-C - paste the result (address from an order) to a document with formatting & company logo, and send it to printer...

All this can be automated in windows using promixis's Girder, unisyn's Automate, and other products...

how can it be done in Linux ?

Thank you.

---

### Post by tamoneya on 2008-05-05
I think most advanced linux users will automate via command line.  The command line is much more powerful and advanced users are able to take control of this power.  It is a lot simpler to just deal with text than to say move mouse here, double click, ctrl-c.

---

### Post by Andre-D on 2008-05-05
Ok- I have nothing against command line.
So.

My webshop is administrated via a WEB-page. (FireFox)
Is it possible, via command line, to get some text selected/copied from a certain place in webpage that FireFox is displaying.. and copy it to labelprinter, envelope/printer and so on?

I also want to clink some links and print the invoice/packaging-slip automatically upon opening of these links.

Where do I start ? - can such actions really be done from a terminal-window ?

---

### Post by ibuclaw on 2008-05-05
You might want to give [XMacro]("http://xmacro.sourceforge.net/") a try.

It can record keyboard and mouse actions/events from within the current x-server window. From which you can save and run whenever you wish.

It's in the repos:
```
sudo apt-get install xmacro
```

Give it a whirl, and see what you think of it.

Regards
Iain

---

### Post by Andre-D on 2008-05-06
Thanks.
I've tried to use it, but what should I enter for remote_display ?
 
"xmacrorec [options] remote_display"

---

### Post by ibuclaw on 2008-05-06
I think the usage is this:
```

xmacrorec2 > **filename**

```
"**xmacrorec2**" records your screen. xmacrorec on the other hand is for remote display operations.
"**>**" is the bash term to store stream data to a file or location.
"**filename**" is the location where you want the macrodata to be stored.

You'll be asked to type in an exit key (ie: just hit escape).

Then do what you want to do. Hit Esc, to terminate the macrorec app.

To run the macro its the command:
```
cat **filename** | xmacroplay ":0.0"
```

Just a note, I think it the app runs all commands at (what appears to be) once with no apparent pause inbetween.
So when you run the macro, make sure all windows that you need are open.
(ie: if you open a program like gedit in the macro and copy some text into it. The macro would have been finished by the time gedit allocates the resources to open, so the copied text goes nowhere).

If this could be a nuance to you, try and look up if the app can handle pauses from within its macro file. (May need to look at sourceforge page for that info).

That should be enough info you to get something started on it.

Regards
Iain

---

### Post by Andre-D on 2008-05-06
Hi.
Sure - thanks.
It lacks the option to navigate in coordinates realative to a window, but with pauses added, it seems to be what I need.

Thank you.

---

### Post by rickdane on 2008-09-06
I don't think it lacks the option to navigate with coordinates relevant to a window, rather there are no pauses in between the actions so the script essentially runs much faster than the time it actually took when recording it, so if you open a program by the time the few seconds it takes to start the program have passed the xmacro script has already completed running. To account for this you need to add the following to the script to account for where there should be a pause:

Delay (number of seconds)

---

