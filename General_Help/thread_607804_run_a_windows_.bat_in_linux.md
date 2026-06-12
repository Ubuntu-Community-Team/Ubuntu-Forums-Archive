---
title: "run a windows .bat in linux???"
date: 2007-11-09
forum: General Help
---

### Post by max_power on 2007-11-09
Is it possible to run a windows batch file in linux? Ive tried using WINE and running the file in the terminal but have had no luck.

thanks.

---

### Post by creeco on 2007-11-09
Try to search the web for a .bat to exe converter (there are plenty avaiable.) I recommend you do this is windows, simply because there are a much wider selection of converters avaialbe for it!

---

### Post by tombott on 2007-11-09
What exactly does the batch file do?

---

### Post by max_power on 2007-11-09
**SOLVED**

after thinking about it for a while my best solution was to download DOSBOX which runs on linux and windows. Its in the repositories so it was an easy install. 

in DOSBOX you have to mount the folder your files are in:

mount c \home\chris\Desktop\THEFOLDER\

Run your batch and you are good to go.

FYI my batch file was written before windows had a GUI so its a batch file but more like one of those old school computer programs you see on old machinery.

thanks to those who commented.

---

### Post by tombott on 2007-11-09
Glad to hear you got it solved.
I use DosBox and have written a Batch file that launches on start that gives me a menu for ease of loading old games.
Back to the old skool!

---

### Post by LaRoza on 2007-11-09
I also use batch files on Windows. In fact, I use them every time.

---

### Post by tombott on 2007-11-09
Yeah .bat and .cmd files can be very handy indeed.
I use Robocopy via a .cmd file to backup an entire Novell 6.5 file system and Groupwise system to a windows XP machine for a client. It even emails the log file upon completion!
Before I got into Linux i would always bring up a cmd windows and type, that's where the real power is!

---

### Post by LaRoza on 2007-11-09
> **tombott said:**
> Before I got into Linux i would always bring up a cmd windows and type, that's where the real power is!

I even use Vim in Windows in the command line.

---

