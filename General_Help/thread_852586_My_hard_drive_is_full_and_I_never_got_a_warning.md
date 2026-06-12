---
title: "My hard drive is full and I never got a warning?"
date: 2008-07-07
forum: General Help
---

### Post by QwUo173Hy on 2008-07-07
I didn't realize my hard-drive was getting full and all of a sudden programs starting acting funny. For example Firefox bookmarks were gone. I've deleted some stuff and now the system is back to normal, but I would have expected to be warned of something like this. Is this a bug I should report? I didn't find anything in launchpad or on this site, which really surprises me.

Regards,
Jarlath

---

### Post by jamesapnic on 2008-07-07
Its not a bug, you would need to create your own scripts to be warned of such.  However maybe you could ask for this feature? :)

---

### Post by QwUo173Hy on 2008-07-07
Thanks James. I'll put it on the wishlist!

---

### Post by forger on 2008-07-07
you could try cleaning up a bit:
```
sudo apt-get autoclean
```

and Places > Recent Documents > Clear Recent Documents

also give your vote to: [http://brainstorm.ubuntu.com/idea/57/](http://brainstorm.ubuntu.com/idea/57/) :)

---

### Post by QwUo173Hy on 2008-07-07
Thanks forger. The autoclean alone gave me back 300MB! I'd forgotten how many updates there have been.

I've added my vote to that feature too.

All the best,
Jarlath

---

### Post by Bubba64 on 2008-07-07
You can check whats available with disc usage analyzer in accessories.

---

### Post by QwUo173Hy on 2008-07-07
Thanks Bubba, I was aware of that and the System Monitor tool, but neither were any use to me once the system got full. Thankfully, my system didn't crash so I just deleted the last movie I had ripped on to my computer.

---

### Post by forger on 2008-07-07
Here's a quick perl script:

```
perl -e '$threshold = 90; @input = `df -Th`; foreach $item (@input) { if ($item =~ m/^([^\s]+)\s.*\s(\d\d?\d?)%\s/ && $2 > $threshold) { $all = $all.$1." ".$2."% "; } } if ($all !~ m/^[\s%]*$/) { `zenity --text "The following devices were found to have less than the allowed free disk space:" --list --column "Device" --column "Used disk space (%)" $all` }'
```

You could put it in a bash script and use it in a crontab to run every 5 minutes or so :)

Change $threshold = 90 to your liking, 90 means that it will show the error if any filesystem is **using 90% or more** of its disk space (which means it has only 10% free space left).

---

### Post by RaveJunkie on 2009-05-29
My pc has four HDD's and my root was full, i know is bad but didnt notice till firefox acted goofy and could not get virtual box to launch.   Auto clean fixed my issue and i also run "conky" on my desktop

I run "hellanbz" alot and even just the /tmp folder on that can grow out of hand.  I wish nautilus or whatever would have a drive quota option like winblows......

---

### Post by binary10 on 2009-05-29
> **RaveJunkie said:**
> My pc has four HDD's and my root was full, i know is bad but didnt notice till firefox acted goofy and could not get virtual box to launch.   Auto clean fixed my issue and i also run "conky" on my desktop

I run "hellanbz" alot and even just the /tmp folder on that can grow out of hand.  I wish nautilus or whatever would have a drive quota option like winblows......

I was also going to mention conky to monitor your partitions, just configure it to your needs and maybe add a 10minute check on your own personal usage if you're need that sort of info

```
 Home area usage: ${execi 600 du -hsx /home/your-usr-name}
```

Gives you something to look at when you got a blank screen :)

---

