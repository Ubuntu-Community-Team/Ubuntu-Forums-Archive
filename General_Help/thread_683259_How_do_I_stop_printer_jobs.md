---
title: "How do I stop printer jobs?"
date: 2008-01-30
forum: General Help
---

### Post by ka1eui on 2008-01-30
I have 25 jobs pending on the printer and it is not printing.  I want to be able to cancel them ALL.   
I am pretty new to Ubuntu.  I would really appreciate it if one of you kind folk would walk me step by step on how to completely cancel every print job.

Thank you in advance

---

### Post by lizadove on 2008-01-30
When you start a print job you should be able to find a little printer icon in your tray area somewhere.  Click/Double-click that and it will open the details of the print jobs.  You can then highlight the jobs (I'm not sure if you can do them all at once, but you could try), right-click and select "X Delete".  It's pretty similar to the Windows printer control panel.  

I hope that's what you were looking for.  Good luck!

---

### Post by lizadove on 2008-01-30
Also.... ha, I had the same problem and silly me, I had the USB unplugged, though I thought I could see it peeking out from behind the CPU.  So.. don't forget to check the basics. ;)

---

### Post by ka1eui on 2008-01-30
My USB cables are all plugged in fine...and I have no Icon in the Tray....I wish I did have an icon!  How can I get one there?

---

### Post by lizadove on 2008-01-31
Okay, let's see if this works.  When you go to print your next page (just hit Ctrl+P) look at your "System Options" button before you click anything else.  That should bring up a Print Configuration window.  At the bottom, under "misc" there's a box you can check to say "Show printing status message box".  I think if you check that box you should.... get an icon. Give it a try and let me know - maybe something else in that control panel will change what you need.

---

### Post by ka1eui on 2008-01-31
When I hit CTRL P I get a box that says Print at the top ...it lists the printer name, properties, print range, copies, print Frames but no "System Options" button.  Is there another way to find that "System Options" button?  That sounds like it's exactly what I need.
Thanks for trying to help me

---

### Post by Fraktyl on 2008-01-31
Try this in a terminal:

```

lpstat -v

```That should give you your printer name.

```

cancel -a [printer name from previous step]

```

You may have to do a sudo for the cancel command.  Not positive on that one.  If it errors on you, just add sudo before the cancel.

---

### Post by ka1eui on 2008-01-31
I was hoping someone would know a command line approach.  I think we are getting closer but I still am unclear of exactly the device name that I should type in,  I have attached a screen shot
Thanks so much

---

### Post by Fraktyl on 2008-01-31
Looks like you've got 2 printers there.  Try this command:

```

lpq

```That should show you which printer has jobs in the queue.  Then use the "cancel -a" command with that printer.

For the name, from the screen shot, it would be either: Stylus_CX7400 or Stylus_CX74002

---

### Post by ka1eui on 2008-01-31
I did it...and now when I type lpq I get:      no entries

It looks like we did it yes?

If so THANKS!

I have to run out and take the ferry to Nantucket for the day so I won't be here to get your answer probably until tomorrow.  Thanks in advance for your help!  I really appreciate it

Jim

---

### Post by Fraktyl on 2008-01-31
If lpq has nothing listed, then yes your queues are cleared.  :)

Glad I could help.

---

### Post by Kevbert on 2008-02-01
Thanks, I had a print job queued from yesterday!!!

---

