---
title: "Bizarre problem with downloading file."
date: 2008-06-25
forum: General Help
---

### Post by AndrewCooper on 2008-06-25
I'm running Heron (newly installed) on an IBM T43 laptop.  I decided I wanted to download the openSuse Live CD ISO to give it a looksee.  So, I started downloading the file with Firefox.  Well, towards the end of the download an error message pops up saying that the download can't save the file because the Download folder is write protected.  I navigate to my Home folder and sure enough every folder in there has the little padlock symbol on it indicating that they are write protected.  I right-click on the Download folder and click on Properties and my window closes instead of opening a new window.  I reopen and attempt to rick-click again.  This time a completely blank window opens.  Nothing in there at all.  

I can click on any folder and get the same result.  Blank window.  Now when I attempt to restart the computer, the icons are gone from the Quit dialogue and the computer won't restart.  I have to literally turn the computer off with the power button to get it ot shutdown.  Then I turn it back on, log on and then can restart it with a proper shutdown.

It does this every time.

Anyone know what is going on and why?

Andrew

---

### Post by iaculallad on 2008-06-25
You don't own your own home directory?

Drop to your terminal and issue the command below:

```
ls -l -d /home/your_user_name
```

What does the command display?

---

### Post by AndrewCooper on 2008-06-26
> **iaculallad said:**
> You don't own your own home directory?

Drop to your terminal and issue the command below:

```
ls -l -d /home/your_user_name
```

What does the command display?

I'm back at work right now so I can't get to my Ubuntu box.  Since posting this message I've rebooted and gotten back to a state where I can access my directories again.  When I get home I'll redo the steps that cause things to mess up and try what you're suggesting.  However, if I remember what I tried last night correctly, I won't be able to get to the terminal.  I believe all my program launchers quit working and just brought up blank windows.  All this makes it really hard to describe, obviously, because I can't even get a screenshot when it is screwed up.

Andrew

---

### Post by AndrewCooper on 2008-06-26
By the way, cute kiddo in your avatar.

Andrew

---

