---
title: "broth 2240 hl printer driver"
date: 2017-11-13
forum: General Help
---

### Post by chris15491 on 2017-11-13
i went through the ubuntu help sections and found instructions.. however i am not compter savy enough to fix.  i entered  [COLOR=#000000]cd ~/Downloads in the terminal and got 
[/COLOR]cd ~/Downloadschris@chris-desktop:~/Downloads$  gunzip linux-brprinter-installer-Linux-brprinter.installer-2.1.1-1.gz

i put this command in to open this file or at least grab it and 
it says  


 No such file or directory
gzip: 1.1.gz: No such file or directory
gzip: gz.gz: No such file or directory
 what am i doing incorrectly?

i tried parantheses and then read no us  quotation marks

---

### Post by chris15491 on 2017-11-13
i'm tryingto follow this 
Step1. Download the tool.(linux-brprinter-installer-*.*.*-*.gz)

The tool will be downloaded into the default "Download" directory.
(The directory location varies depending on your Linux distribution.)
e.g. /home/(LoginName)/Download

Step2. Open a terminal window and go to the directory you downloaded the file to in the last step.

Step3. Enter this command to extract the downloaded file:

Command: gunzip linux-brprinter-installer-*.*.*-*.gz

Step4. Get superuser authorization with the "su" command or "sudo su" command.

Step5. Run the tool:

Command: bash linux-brprinter-installer-*.*.*-* Brother machine name

Step6. The driver installation will start. Follow the installation screen directions.


 When you see the message "Will you specify the DeviceURI ?",

 For USB Users: Choose N(No)
 For Network Users: Choose Y(Yes) and DeviceURI.

The install process may take some time. Please wait until it is complete.

---

### Post by chris15491 on 2017-11-13
By a miracle . i got this to upload and work.. it takes a bit t to learn the commands when you are  new  to linux.. thank you to all the kind people who post info and answers on this forum.. as a new user and learner it is VERY helpful.. chris

---

### Post by ajgreeny on 2017-11-13
That is great news! Well done for figuring it out.

Please mark as SOLVED from the Thread Tools menu up-top if this is now solved to your satisfaction. It is a great help to users searching the forum.

---

