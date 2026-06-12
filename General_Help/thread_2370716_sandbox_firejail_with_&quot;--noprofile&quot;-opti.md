---
title: "sandbox firejail with &quot;--noprofile&quot;-option"
date: 2017-09-06
forum: General Help
---

### Post by rosika on 2017-09-06
Hi,


I´ve created a portable version of the opera-browser (see  [https://gist.github.com/ruario/8416e36372f1a976a713](https://gist.github.com/ruario/8416e36372f1a976a713) ).


In order to open it I´ve got to type the command "opera-developer_27.0.1670.0_amd64/run &" in the respective directory.
This works quite well. But when trying to run it within firejail using the command "firejail opera-developer_27.0.1670.0_amd64/run &" it won´t work.


Using the "--noprofile"-option however gives me fine results. So "firejail --noprofile opera-developer_27.0.1670.0_amd64/run &" works alright.


Yet what I really want to do is running it with the "--private" option.
So "firejail --private=[path to a specified working directory] opera-developer_27.0.1670.0_amd64/run &" would be nice. 
Yet I found out that this very command cannot work together with the "--noprofile option".


Is there a way to start my portable opera-browser within firejail using the --private-option?


Thanks a lot in advance.


Rosika  :confused:


P.S.:
system: Linux/Lubuntu 16.04.3 LTS, 64 bit

---

### Post by &amp;KyT$0P# on 2017-09-06
Please post the exact terminal output you get from running this command -
```
firejail --noprofile --private=[path to a specified working directory] opera-developer_27.0.1670.0_amd64/run
```

---

### Post by rosika on 2017-09-08
Hi halogen2,

thanks for your reply.

When typing  > [COLOR=#000000][FONT=&amp]firejail --noprofile --private opera-developer_27.0.1670.0_amd64/run[/FONT][/COLOR]

I get the following message:

```
rosika@rosika-Lenovo-H520e ~/D/o/N/8416e36372f1a976a713> firejail --noprofile --private opera-developer_27.0.1670.0_amd64/run &
Parent pid 7000, child pid 7002
rosika@rosika-Lenovo-H520e ~/D/o/N/8416e36372f1a976a713> 
Child process initialized
/bin/bash: opera-developer_27.0.1670.0_amd64/run: Datei oder Verzeichnis nicht gefunden


parent is shutting down, bye...
'firejail --noprofile --private…' has beendet



```

When typing just > [COLOR=#000000][FONT=&amp]firejail --noprofile --private opera-developer_27.0.1670.0_amd64/run[/FONT][/COLOR]

opera-browser starts as required.

Greetings.
Rosika

---

### Post by rosika on 2017-09-09
Hello again,

seems like there was some sort of misconception on my part.
When using the "--private"-option firejail seems to have no access to the  folder from where I start the opera-browser.
Thinking of it this makes sense as "--private" represents the highest degree of security firejail can produce.

So I did the following:

I created a dedicated folder named "opera-browser" within my "work"-directory (which I already use for firefox etc. together with the "--private"-option).
My new command is:

```
firejail --noprofile --private=/home/rosika/Schreibtisch/work/opera_portable/ opera-developer_49.0.2695.0_amd64/run &
```

This one works as desired. And it has the additional benefit of keeping my add-ons and settings. I´m glad I could solve this problem.


So thanks again for your help an many greetings.

Rosika  :p

---

