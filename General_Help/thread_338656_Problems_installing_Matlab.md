---
title: "Problems installing Matlab"
date: 2007-01-14
forum: General Help
---

### Post by evanmanny on 2007-01-14
Hello. I'm trying to install Matlab on my system which is running Edgy. It spits out:

[INDENT]Error installing MATLAB for Linux (x86)

Error installing MATLAB for All

Error installing Simulink for All

Error installing Simulink for Linux (x86)[/INDENT]

When I search google for "Error installing MATLAB" I don't get a single hit. Despite the errors, the install continues as it should and eventually finishes. Then when I try to run matlab it gives me:

[INDENT]matlab: No MATLAB executable for this machine architecture.

/mnt/common/matlab/bin/glnx86/MATLAB does not exist!
[/INDENT]
I know that this is ultra vague, but has anybody had a similar experience? I just don't know where to go from here.

Thanks
Evan

---

### Post by spaznrq on 2008-02-01
It is unfortunate that no one has posted a response with an answer to your question, as this is exactly what I am experiencing with Matlab 7.4 (2007a) on my Ubuntu 7.10.

I'm doing a reinstall with none of the Matlab libraries removed to see if that fixes things...

---

### Post by pointone on 2008-02-01
You're installing it as root, of course?

---

### Post by spaznrq on 2008-02-01
> **pointone said:**
> You're installing it as root, of course?

definitely.  i used "sudo ./install".  i installed matlab to "/etc/matlab74", and it wouldn't have let me create that folder if i wasn't with root permissions.

thanks.  other ideas?

---

### Post by spaznrq on 2008-02-01
oh just to provide more info..

i followed the installation manual in PDF that was included with Matlab, and the installation wizard skipped step 11.  this step is to "specify location of symbolic links", supposedly giving me a dialog to enter the location of the symbolic link creation.  also, it wouldn't give me the window to enter login names to be allowed permissions to run matlab.  it merely goes straight to step 12 with "Begin Installation?" with a "OK" "Cancel" and "Help".

i bet this was what is missing to get it to work, but the Matlab installer just wouldn't give me this window no matter how i configure it while installation.

---

### Post by TerpInHotLanta on 2008-02-07
Here is what I have found in the 20 hours it took me to get MATLAB up-and-running:
(Sorry if this is really pedantic to some of you all-- but I figure mega-newbies need all the spoon-feeding they can get)

Are you installing 2007a?
Note: this is the 32-bit version

Is your computer 64-bit? (Mine was)

Here's how I installed 32-bit MATLAB on my system, which is 64-bit (NB: I found the other solutions-- including Mathworks' own solution to be junk)

1. From the "unix" directory on the install CD (haven't tried it as a normal user-- used the root shell)

./install -glnx86

2. After it's installed you'll get some warnings of sorts. Go to the installation directory (/usr/loca/matlab2007a in my case):

./install_matlab -glnx

Answer 'y' to all questions (this takes care of the license stuff)

3. From the matlab home go to sys/java/jre

cp -r glnx86 glnxa64

Use symbolic links if you'd like

This tricks the matlab script into thinking there is a 64-bit java jvm-- turns out it doesn't matter-- they all act the same

4. In the same directory as the matlab file (e.g. /path/matlab2007a/bin/) create a file (I called it matlab2 -- or you can call it matlab2.sh)
In this file have

export AWT_TOOLKIT=3DMToolkit
/usr/local/matab2007a/bin/matlab

5. In the terminal
chmod 755 matlab2

6. Run matlab (should be doable from any user's account if the installation is in usr/local)

From the matlab directory

./matlab2

NOTE:
*If MATLAB opens but there are no icons, make sure the AWT_TOOLKIT  is spelled correctly (it is CASE SENSITIVE)
*I found that using the export MATLAB_JAVA command that so many other people talked about gave me a command-line MATLAB system, but the GUI didn't work at all
*If you tried alternate JVM's before, and now the GUI isn't working after following my steps, try

export -n MATLAB_JAVA

I really hope this helps, as this problem frustrated the INSERT MANY EXPLETIVES HERE out of me.

---

### Post by punkdaily on 2008-05-19
Thanks for this, this finally got me going.

I've just spent 5 hours getting this to work.

One other note, this might not affect everyone, but it appears that for the student version Matlab gets your "hostID" from your eth0. In my case, I had removed a nic card, and not re-assigned eth0, so the license file didn't work.

This is only a major issue with 32 bit matlab on a 64 bit linux because the license manager software won't run on 64 bit linux.

---

