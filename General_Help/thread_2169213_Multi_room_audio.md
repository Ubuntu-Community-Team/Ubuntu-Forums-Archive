---
title: "Multi room audio"
date: 2013-08-21
forum: General Help
---

### Post by badgerbailey2 on 2013-08-21
Hello,

I am trying to set up a multi room audio solution which I have successfully completed using this guide: [http://www.avsforum.com/t/1350118/running-multiple-softsqueeze-streams-from-one-pc](http://www.avsforum.com/t/1350118/running-multiple-softsqueeze-streams-from-one-pc) however it uses windows as the guide, I want to use ubuntu as the server for reliability but when the guide gives examples of creating batch files, I understand that ubuntu would not be able to understand these.

Here is a copy of the example batch file:

@echo off
start /min "PC Speakers" java -Dserver=localhost:9000 -Dskins=headless -Daudio.mixer="Speakers (High Definition Audio Device)" -Dmacaddress=f7:25:9d:78:9f:66 -jar Softsqueeze.jar
exit


how would I convert this so ubuntu would understand which softsqueeze instance to map to which soundcard?

Is it possible, the guide mentions that it is but without much guidance,

Thanks in advance for your help.

Regards,

Badgerbailey

---

### Post by lukeiamyourfather on 2013-08-21
I'm not familiar with that software but it looks like it's just launching a headless server application. So it would look something like this.

```

#!/bin/bash
java -Dserver=localhost:9000 -Dskins=headless -Daudio.mixer="Speakers (High Definition Audio Device)" -Dmacaddress=f7:25:9d:78:9f:66 -jar Softsqueeze.jar

```

---

### Post by tgalati4 on 2013-08-21
Let us know how it works.  I'm curious about the audio latency between adjacent rooms.

---

### Post by badgerbailey2 on 2013-08-21
I will try it out today to see what happens, it does work very well under windows so I imagine it will be just as good or better under linux

---

### Post by badgerbailey2 on 2013-08-22
Unfortunately it didn't work with that script, I just get the error message saying failed to execute child process no such file or directory, any idea why this would be?

---

### Post by lukeiamyourfather on 2013-08-22
> **badgerbailey2 said:**
> Unfortunately it didn't work with that script, I just get the error message saying failed to execute child process no such file or directory, any idea why this would be?

Sounds like you don't have a Java runtime environment installed if the message came from the shell. Can you post the exact message including the command prompt? It also might not be seeing the JAR file, so you could give it the full path to the file (otherwise you have to run it from the directory where the JAR file is).

---

### Post by badgerbailey2 on 2013-08-22
Yes I actually installed java runtime openjdk 7, then I installed softsqueeze in the home directory in its own folder, then I created 5 text files with the extension .sh to be used as the scripts for starting the softsqueeze. These are in the softsqueeze folder, (bed1.sh, bed2.sh, master.sh, living.sh and outside.sh) I can start softsqueeze from the command prompt but I need to make the scripts which will select which usb soundcard to use. I will post the exact error message soon.

---

### Post by badgerbailey2 on 2013-08-23
Added some more detail:

Hello,

I am trying to set up a multi room audio solution which I have successfully completed using this guide: Running multiple Softsqueeze streams from one PC

[SIZE=2][COLOR=#2F4F4F][I]Detailed instructions:

 

1. Install Squeezebox server and Softsqueeze. It helps to install both in a non-protected directory in Windows 7. This prevents requiring admin rights to do everything.

 

2. Install Java JDK. This is required to run Softsqueeze from the command prompt.

 

3. Run Softsqueeze from the command window and turn on the Configuration debugging options. 

- If you are getting an error trying to run from the command line, make sure .jar is associated with the Java JRE by following instructions here.

- Open a command window to the Softsqueeze install directory and enter the following command to run it: java -jar SoftSqueeze.jar

- Softsqueeze will run in two windows - the command (DOS) window and the GUI. In the GUI hit the Preferences button and go to the Debug tab. Tick the Configuration box. Now any changes you make in preferences will be logged to the command window.

- Again in preferences, go to the Audio tab and change the Audio Mixer. This lists your sound devices. Select each one in turn and the details of each will be logged in the command window. The EXACT text describing each device is used in the next step.


4. Create a batch file that launches a "headless" (i.e. no GUI) Softsqueeze instance with your configuration options. A separate batch file is created for each audio device/zone. Copy the below text into notepad, edit and save as .bat.
Code:

@echo off
start /min "PC Speakers" java -Dserver=localhost:9000 -Dskins=headless -Daudio.mixer="Speakers (High Definition Audio Device)" -Dmacaddress=f7:25:9d:78:9f:66 -jar Softsqueeze.jar
exit

A batch file needs to be created for each sound device you want to use, and put in the Softsqueeze directory. From the above example, change PC Speakers to the device name (e.g. a soundcard connected to an amp powering the kitchen speakers could be called Kitchen), the audio device name to what you got from step 3 and choose a random MAC address (each device needs a different virtual MAC).

4. Configure the device names in Squeezebox server. Run the Squeezebox server and then all the batch files to launch the players. Then, from a web browser, go to localhost:9000 and click on Settings (lower right corner). Under the Player tab, select each Softsqueeze from the drop down and re-name to match the zone. This name will be permanent as it will be associated with the zone's unique MAC address as set above.

5. From now on, just launch the batch files from shortcuts or Startup folder along with Squeezebox server and all the audio devices will be running and configured![/I][/COLOR][/SIZE]

(sorry to add entire post but I can't paste links)

however it uses windows as the guide, I want to use ubuntu as the server for reliability but when the guide gives examples of creating batch files, I understand that ubuntu would not be able to understand these.

Here is a copy of the example batch file:

@echo off
start /min "PC Speakers" java -Dserver=localhost:9000 -Dskins=headless -Daudio.mixer="Speakers (High Definition Audio Device)" -Dmacaddress=f7:25:9d:78:9f:66 -jar Softsqueeze.jar
exit


how would I convert this so ubuntu would understand which softsqueeze instance to map to which soundcard?

Is it possible, the guide mentions that it is but without much guidance,

I tried to follow someones advice and create a shell script with these contents:

#!/bin/bash
java -Dserver=localhost:9000 -Dskins=headless -Daudio.mixer="Speakers (High Definition Audio Device)" -Dmacaddress=f7:25:9d:78:9f:66 -jar Softsqueeze.jar

But when I try to start the script from within the same folder as the softsqueeze.jar I get failed to execute child process no such file or directory, although I am running this from within the same directory.

Would anyone have an idea how to get this working so that I can use the 5 different soundcards as I really need it up and running. It works with no issues under windows, I know that java runtime is installed correctly because I can start the softsqueeze.jar from command line with no problems.

Looking forward to an answer,

Thanks in advance,
Badgerbailey

---

