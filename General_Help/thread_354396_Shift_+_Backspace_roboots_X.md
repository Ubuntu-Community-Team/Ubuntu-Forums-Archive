---
title: "Shift + Backspace roboots X"
date: 2007-02-05
forum: General Help
---

### Post by banditti on 2007-02-05
Shift + backspace reboots X.  I think it is a Beryl issue.  Thoughts?

---

### Post by Freaky_Llama on 2007-02-05
does it do the same thing as ctrl-alt-backspace?

I'd go as far as checking the beryl-manager for a mapping to those keypresses and see what it does. You may be onto something that could cause an X restart.

I'd also check logs to see if any errors appear.

---

### Post by banditti on 2007-02-05
I forgot to add I get a crash report!

---

### Post by banditti on 2007-02-06
Can I get a bump bump?

---

### Post by commonplace on 2007-02-06
Shift+Backspace is the command to restart XGL. Are you running XGL+Beryl?

/Kevin

---

### Post by kebes on 2007-02-06
> **banditti said:**
> Shift + backspace reboots X.  I think it is a Beryl issue.  Thoughts?

This is a known Beryl issue. There is an option somewhere to work-around this behavior... Try searching the Beryl forums for a solution. For instance a quick search came up with this:

[http://forum.beryl-project.org/viewtopic.php?f=39&t=245&p=1295](http://forum.beryl-project.org/viewtopic.php?f=39&t=245&p=1295)

Hope that helps.

---

### Post by commonplace on 2007-02-06
See [this post]("http://ubuntuforums.org/showpost.php?p=1999608&postcount=12").

/Kevin

---

### Post by banditti on 2007-02-06
That did it.  Thanks.

---

### Post by banditti on 2007-02-08
After updates today, it doesn't work anymore.

---

### Post by commonplace on 2007-02-08
> **banditti said:**
> After updates today, it doesn't work anymore.

Beryl updates, or the kernel updates, or...? I haven't installed the new kernel that was just pushed out, yet, but I did install the Beryl updates. I'll have to test the Shift+Backspace thing again to make sure it's still working for me. As far as I know, it's okay. Maybe the kernel updates somehow messed it up, though I don't see why it would.

/Kevin

---

### Post by banditti on 2007-02-08
Not sure why either.  I am speaking to the kernel upgrades this morning.  I don't think there were Beryl updates in there, but I didn't pay that much attention.

---

### Post by commonplace on 2007-02-08
Okay, just making sure. (I have Beryl via SVN, so I get updates every day.)

Now I'm having second thoughts about installing the kernel updates tonight!

Anyone else experiencing this as well?

/Kevin

---

### Post by banditti on 2007-02-12
anyone?

---

### Post by commonplace on 2007-02-12
> **banditti said:**
> anyone?

I installed the kernel updates, and my shift+backspace fix still works (as in, it doesn't do anything, which is what I want).

So I don't know if the updates broke it for you or not, but it's still fine for me, at least.

/Kevin

---

### Post by banditti on 2007-02-14
Do you think it would kill anything to switch to getting my updates via SVN?  If not, how do you think I should go about it?


Thanks,

---

### Post by banditti on 2007-02-14
I did it.  It didn't fix my problem, but man what a difference in performance.  It is much quicker and the graphics are better.  Who knew?

---

### Post by commonplace on 2007-02-14
I'm glad it worked out for you! The day I decided to install Beryl (many months ago), the repos were down. I was impatient, so I just went ahead and went the SVN route, and it's worked great for me.

What process did you end up following in order to switch? Just in case others out there want to switch.

/Kevin

---

### Post by banditti on 2007-02-14
I followed the following for the SVN:
[http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_from_the_SVN_snapshots_repository]("http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_from_the_SVN_snapshots_repository")

General Ubuntu Install docs:
[http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu]("http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu")


I still have the SHIFT + Backspace issue.

I also have a new one which is SHIFT + TAB, puts a mini window on my cursor that I can only get rid of by hitting shift again.  I want it to tab backwards like normal.

---

### Post by banditti on 2007-02-14
Correction:  I had the SHIFT + Backspace issue.  The following fixed it:




Add this to the System->Preferences->Sessions->Startup Programs:

```
xmodmap /usr/share/xmodmap/xmodmap.us
```


Not sure why the ~/.bashrc fix stopped working, but oh well.

---

