---
title: "[SOLVED] Making batch files?"
date: 2008-01-06
forum: General Help
---

### Post by fireworld2406 on 2008-01-06
Hi!
     I was wondering how to make batch files. I have a laptop without a hard driver, and until yesterday no USB support. I fixed the USB and bought a USB wireless adapter that works, but as I am limited to the live cd, I think it would be easier for me to make a batch file that executes the commands I need and save it to my flash drive. In Windows, I can make a BAT file that has regular DOS commands. Is it similar in Linux?

---

### Post by p_quarles on 2008-01-06
I guess you're looking for a shell script. You can create one of these by using the text editor. The first line needs to be:
```
#!/bin/bash
```
followed by the commands that you want the script to execute. 

Before you can run the script, though, you'll need to make it executable:
```
sudo chmod u+x /path/to/script
```

---

### Post by fireworld2406 on 2008-01-06
Thank you so much! That's exactly what I'm looking for!

---

