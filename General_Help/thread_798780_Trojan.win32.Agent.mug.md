---
title: "Trojan.win32.Agent.mug"
date: 2008-05-18
forum: General Help
---

### Post by bdmmem on 2008-05-18
Tried several times to use Wubi to install Ubuntu on my windows machine.  My Zone alarm virus/spyware insists that the above Trojan is being downloaded and shuts down the process.

Any thoughts?

---

### Post by ivze on 2008-05-18
Google says nothing about this trojan. Strange.
Apart from that, it is possible that you have downloaded a hacked .exe. Check it's md5sum (how to check md5sum on windows - don't know now, but this task is definitely solvable).

---

### Post by ivze on 2008-05-18
A nice windown app for generating md5 sums [http://www.md5summer.org/download.html](http://www.md5summer.org/download.html).
MD5SUMS can be found here (and in many other locations) [http://ftp.u-picardie.fr/mirror/ubuntu/releases/8.04/MD5SUMS](http://ftp.u-picardie.fr/mirror/ubuntu/releases/8.04/MD5SUMS) .
You need to check your wubi.exe installer.

---

### Post by bdmmem on 2008-05-18
First I down loaded off Wubi site and then off the development sourceforge site.  Same result.  Does not cause a problem until it starts downloading Ubuntu 8.04.

---

### Post by ivze on 2008-05-18
Nice situation! Folks, wubi is thinked to be a trojan by Zone Alarm =P.

The solution for you, bdmmem, is to turn off the antivirus temporarily.

---

### Post by ago on 2008-05-18
Well wubi source is open, so it should be easy to double check.

Do this excercise.

Go into your user temp folder (type %temp% in explorer), and delete all the temp folders in there.

Run wubi, but do not press install. 

Wubi creates a temporary folder where it extracts all its files in your user temp folder. You will see this as a new temp folder (deleting all the other folders will make it easier to spot it).

Run whatever antivirus on that folder and see if any of the extracted files generates problems.

---

### Post by bdmmem on 2008-05-18
The Wubi file does not appear to be the problem. Scanned the Temp directory - the problem arises as soon as the install starts.

I actually went through a complete install yesterday with no virus warnings.  But could not get ubuntu to run. Uninstalled and updated my bios and was going to try again when started getting warnings.  Zone Alarm say that the risk level is high.

---

### Post by abn91c on 2008-05-18
you probably have viruses in your PC. go to the symantec website and run Their online security or antivirus scan, you may want to run spybot also. If you have a 7.10 live cd or a 8.04 live CD wubi is included in the cd

---

### Post by drifter0000 on 2008-05-19
I use 3 virus and or malware clients running at the same time in windows xp Pro Sp2 and I defrag my C: drive everyday.  Basically thats why I use Hardy 8.04.  I put xp back on my hard drive so that I could use Acronis True Image to back up my entire drive.  When I installed Hardy it was too difficult to back up with True Image so I thought I would try wubi.

I created a separate 15gb NTFS Partition and pointed Wubi to it.  It downloaded and installed perfectly just like unetbootin does only easier.

I did this 4 days ago and had no problems with virus detection.  I very nice clean install that left my Windows Boot Sector intact so I can do back ups.  I made the install with 2 anti-virus running and firewall running....my firewall is Comodo so it is also actively watching installs.

I had no problems with install at all.

About a year ago I quit using Zone alarm products because of system slow downs and false dectections. I would say Zone alarm is your problem.

---

### Post by ago on 2008-05-19
We had another false-alarm case recently: [https://bugs.launchpad.net/wubi/+bug/229548](https://bugs.launchpad.net/wubi/+bug/229548)

Same holds here. Most likely the av heuristic is wrong, not much we can do on our side. The best course of action is to notify the av producer so that they can rectify their heuristics.

---

