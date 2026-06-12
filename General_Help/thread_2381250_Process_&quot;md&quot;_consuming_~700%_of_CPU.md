---
title: "Process &quot;md&quot; consuming ~700% of CPU"
date: 2017-12-28
forum: General Help
---

### Post by Austin_Kargl on 2017-12-28
Hey, everyone. I have a build I made running Ubuntu Server (No GUI) 16.04 LTS and use it to run a small ARK:SE Server. Everything has seemed great up until today when I noticed that the server seemed pretty slow. After using PuTTY to ssh into the server, I noticed that the CPU was nearly pegged.

[IMG]https://imgur.com/3Uwiq3L[/IMG][IMG]https://i.imgur.com/3Uwiq3L.png[/IMG]

After researching process "md", it appears it has to do with RAID Controllers? This is a single-disk server with no other drives, only running on a 128GB Toshiba SSD. If I kill, shut down and power on, reboot the server, or even kill the process it just comes back under the Steam user (who, by the way, is not an administrator on the machine). The reason I'm not posting this on an ARK:SE Forum is because I don't have reason to believe that steamcmd or [ASM]("https://github.com/FezVrasta/ark-server-tools") is causing this. This server has been live for 10-12 days and this problem just started today amidst the server already running.

Is anyone familiar with this process, and why it may be draining the CPU? If it's helpful, the CPU is a Intel i7-4770K.

Thanks for any input that you may have, I appreciate it.

---

### Post by Austin_Kargl on 2017-12-28
[U][B]Update
[/B][/U]It looks like my computer was targeted via SSH and is being used for Cryptomining. After using "killall md", they reappear after 20-30 seconds. I'm currently looking for the script being used to restart the mining process.

---

### Post by Austin_Kargl on 2017-12-28
> **Austin_Kargl said:**
> [U][B]Update
[/B][/U]It looks like my computer was targeted via SSH and is being used for Cryptomining. After using "killall md", they reappear after 20-30 seconds. I'm currently looking for the script being used to restart the mining process.

[U][B]Final Update
[/B][/U]The rest of this is irrelevant to the topic I posted about, but perhaps it will help someone that is silly like me and uses a garbage password for an ssh-authorized account (steam).

One of my good friends was able to help me with a couple of commands to find the location. For reference, the PID of "md" is going to be '2024'

```
austin@server:~$ sudo ls -l /proc/2024/exe
lrwxrwxrwx 1 steam steam 0 Dec 28 20:33 /proc/2024/exe -> /home/steam/.ssh/.cuz/md
austin@server:~$ ls /home/steam/.ssh/.cuz/ -a
.  ..  a  bash.pid  cron.d  dir.dir  h32  h64  md  mdx  run  runx  upd  x
austin@server:~$ sudo rm /home/steam/.ssh/.cuz/ -rf


```

Since running this code, the application has not restarted. Due to the fact that cronjobs may still have been created, I'm going to look into removing those and document what I did to fix it.

---

### Post by Austin_Kargl on 2017-12-28
> **Austin_Kargl said:**
> [U][B]Final Update
[/B][/U]The rest of this is irrelevant to the topic I posted about, but perhaps it will help someone that is silly like me and uses a garbage password for an ssh-authorized account (steam).

One of my good friends was able to help me with a couple of commands to find the location. For reference, the PID of "md" is going to be '2024'

```
austin@server:~$ sudo ls -l /proc/2024/exe
lrwxrwxrwx 1 steam steam 0 Dec 28 20:33 /proc/2024/exe -> /home/steam/.ssh/.cuz/md
austin@server:~$ ls /home/steam/.ssh/.cuz/ -a
.  ..  a  bash.pid  cron.d  dir.dir  h32  h64  md  mdx  run  runx  upd  x
austin@server:~$ sudo rm /home/steam/.ssh/.cuz/ -rf


```

Since running this code, the application has not restarted. Due to the fact that cronjobs may still have been created, I'm going to look into removing those and document what I did to fix it.

**_Solution_**
The silly hacker installed the cronjob in the same folder as the bash scripts.

```
crontab -u steam -e
```
I then selected "3" for Vi Basic and deleted the first and only line, which was a cronjob to execute the script. After deleting the job, saving it with [COLOR=#800000]:w![/COLOR] and exiting vi with [COLOR=#800000]:q[/COLOR], I restarted the server and the process no longer executes. All in all, this was a really fun learning experience.

---

