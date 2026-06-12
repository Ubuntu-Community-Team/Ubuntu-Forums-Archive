---
title: "Fetching system resources per process group through CLI"
date: 2014-01-13
forum: General Help
---

### Post by proxess on 2014-01-13
I've got a pretty nifty CLI one liner which will fetch me process names and their RAM (or CPU) and sum it all up (say for instance you have more than one php-fpm process).```
ps aux | grep -v '\[' | awk 'NR != 1 {x[$11] += $4} END{ for(z in x) {print z, x[z]"%"}}' | sort -k2,2r
```

[LIST]
[*]**ps aux** gets the process list.
[*]**grep** removes system processes. Ex.: [crypto/11]
[*]**awk** gets the process name, the RAM and sums up the RAM. Change $4 to $3 for CPU usage.
[*]**sort** will order from highest RAM usage to lowest.
[/LIST]


Don't forget, 100% CPU = 1 CPU core. It's not abnormal for a process to have 200% CPU usage.

There's an issue I need help with though:
[LIST]
[*]Sometimes command names have delimiters detected by awk that I don't want for it to detect. For instance, *php-fpm: www* and *php-fpm: www-dev* are all detected as *php-fpm*. The only way I know of separating these is *...awk 'NR != 1 {x[$11 $12 $13 ...] += $4}...*. How can I change it to something along the lines of *$11 and all the following*, seeing that process name is all the remaining until line break?
[/LIST]

---

### Post by tgalati4 on 2014-01-13
Nice.  That is a convenient one-liner.  So if I understand this correctly, you want to breakout all of the different php-fpm processes but can't because of the line breaks?  I haven't tested this on a server so it is hard to visualize what is happening.  Perhaps you could post a sample output of what you get and what you want.

My first thought is to pipe the results through another grep:  for instance I only want to see /usr/sbin results:

tgalati4@Mint14-Extensa ~ $ ps aux | grep -v '\[' | awk 'NR != 1 {x[$11] += $4} END{ for(z in x) {print z, x[z]"%"}}' | sort -k2,2r** | grep sbin**
/usr/sbin/cupsd 0.2%
/sbin/dhclient 0.1%
/sbin/init 0.1%
/sbin/wpa_supplicant 0.1%
/usr/sbin/console-kit-daemon 0.1%
/usr/sbin/mdm 0.1%
/usr/sbin/modem-manager 0.1%
/usr/sbin/ntpd 0.1%
/usr/sbin/system-tools-backends 0.1%
/sbin/getty 0%
/sbin/udevd 0%
/usr/sbin/bluetoothd 0%
/usr/sbin/dnsmasq 0%
/usr/sbin/rwhod 0%
/usr/sbin/uptimed 0%

But I get both /usr/sbin and /sbin because of the slash delimiters are ignored.

---

### Post by proxess on 2014-01-13
So what I currently get is:
```
~]$ ps aux | grep -v '\[' | awk 'NR != 1 {x[$11] += $4} END{ for(z in x) {print z, x[z]"%"}}' | sort -k2,2r
/usr/sbin/glusterfs 1.3%
clamd 0.1%
auditd 0%
-bash 0%
bash 0%
cleanup 0%
crond 0%
dbus-daemon 0%
ntpd 0%
php-fpm: 0%
```

and what I'd like to get is:
```
~]$ ps aux | grep -v '\[' | awk 'NR != 1 {x[$11 $12 $13 $14 $15 $16] += $4} END{ for(z in x) {print z, x[z]"%"}}' | sort -k2,2r
/usr/sbin/glusterfs--volfile=/etc/glusterfs/glusterfs-www.vol/var/www 1.3%
clamd 0.1%
auditd 0%
-bash 0%
bash 0%
crond 0%
dbus-daemon--system 0%
ntpd-untp:ntp-p/var/run/ntpd.pid-g 0%
php-fpm:masterprocess(/etc/php-fpm.conf) 0%
php-fpm:poolsupport 0%
php-fpm:poolwww 0%
```

...but without the ugliness of *$11 $12 $13 $14 $15 $16* in the command.

---

### Post by steeldriver on 2014-01-13
Maybe you could attack it from the other end - by trying to get your ps output into a more parse-able format using the o / -o / --format command line switch? For example ,if your ps supports AIX-style output formating you could do something like

```

ps haxo "%C    %a" | awk -F'\t' '$2 !~ /\[.*\]/ {*do stuff*}'

```

where the space between the %C (%cpu) and %a (command with arguments) format specifiers is a literal tab typed as a *Ctrl-v Ctrl-TAB* key combo; or maybe more portably

```

ps haxo %cpu,command | sed -r 's/([0-9]+[.][0-9]+)([[:space:]]+)/\1\t/' | awk -F'\t' '$2 !~ /\[.*\]/ {*do stuff*}'

```

where the space after the %cpu field is replaced by a tab before piping to awk

[I also replaced the grep with a / / regex test inside the awk, and eliminated the need to test NR==1 by suppressing the ps header using the h switch]

---

### Post by tgalati4 on 2014-01-13
True, a one-liner is finished when it is elegant.

A Haiku:

One liner too long?
I need to make it shorter.
Now it's elegant.

---

### Post by proxess on 2014-01-14
That's the most wonderful haiku I've ever come across!!
Unfortunately my command line grew quite a bit. Fortunately, it does exactly as it's told to!

CPU usage:
```
export LC_ALL=C && ps haxo %cpu$'\t'args | grep -v ]$ | awk '{y=""; for (i=2; i<=NF; i++) y=y $i; {x[y] += $1}} END{ for(z in x) {print x[z]"%\t" z}}' | sort -k1g
```
Result:
```
0.1%	php-fpm:pool2
0.9%	/usr/sbin/snmpd-c/etc/snmp/snmpd.conf-LS5d-Lf/dev/null-p/var/run/snmpd.pid
1.3%	top
2.2%	php-fpm:poolsupport
7%	pshaxo%cpu?args
41.4%	php-fpm:poolwww
60%	/usr/sbin/glusterfs--volfile=/etc/glusterfs/glusterfs-www.vol/var/www

```

MEM usage:
```
export LC_ALL=C && ps haxo %mem$'\t'args | grep -v ]$ | awk '{y=""; for (i=2; i<=NF; i++) y=y $i; {x[y] += $1}} END{ for(z in x) {print x[z]"%\t" z}}' | sort -k1g
```
Result:
```
0%	-bash
0.1%	clamd
0.1%	/usr/sbin/glusterfs--volfile=/etc/glusterfs/glusterfs-upload.vol/var/upload
3.9%	/usr/sbin/glusterfs--volfile=/etc/glusterfs/glusterfs-www.vol/var/www
```

Explanation:
[LIST]
[*]**export** is so sort reads the decimals properly.
[*]**ps** is for fetching the processes, this time with a cleaner output.
[*]**awk** does the heavy lifting. We define a variable with the full command and arguments, then sum the percentages of all the seperate processes that have the same name.
[*]**sort** does as it says on the tin.
[/LIST]

Edit: I spoke too soon. I ran the MEM command on a machine that's working hard and it gave me percentages over 100. The same thing happened with the older command. I'd expected this on CPU but not RAM.

New command:
```
1.5%	clamd 
2.4%	php-fpm: pool ru-partner 
15.6%	php-fpm: pool misc 
47.1%	php-fpm: pool photowwwru 
70%	php-fpm: pool wwwru
```

Old command:
```
php-fpm: 134.3%
clamd 1.5%
/usr/sbin/glusterfs 1.2%
```

---

### Post by steeldriver on 2014-01-14
You seem to be trying to use tab-delimiting so how about

```

ps haxo **"%C    %a"** | awk **-F'\t'** '$2 !~ /\[.*\]/ {**x[$2] += $1**} END{ for(z in x) {print x[z]"%\t" z}}' | LC_ALL=C sort -k1g

```

where the 'space' in "%C    %a" is composed as Ctrl-v Ctrl-TAB - that should remove the need to sum over the (space delimited) argument fields

---

### Post by proxess on 2014-01-14
You're right. I was convinced awk's default delimiter was tab so I didn't force a delimiter, then when it didn't work as I had intended, I got creative.

The following works correctly - CPU:
```
ps haxo pcpu$'\t'%a | awk -F'\t' '$2 !~ /\[.*\]/ {x[$2]+=$1} END{ for(z in x) {print x[z]"%\t" z}}' | LC_ALL=C sort -k1g
```

Not so correctly - MEM:
```
ps haxo pmem$'\t'%a | awk -F'\t' '$2 !~ /\[.*\]/ {x[$2]+=$1} END{ for(z in x) {print x[z]"%\t" z}}' | LC_ALL=C sort -k1g
```

From what I've read and understood, the following is why MEM doesn't work as expected:
PS calculates resident set size memory. This includes virtual memory, which is shared between all processes. You never know which part of the virtual memory is accessed at any given time by a process, meaning you're most probably summing memory that you've already summed up, thus the total is blatantly over 100% on hard working machines.

---

### Post by tgalati4 on 2014-01-14
If you use the *free* command you can see how much memory is cached/buffered and compute a ratio or percentage.  That ratio should be close to the overage you are seeing with your memory script.

For example:

tgalati4@Mint14-Extensa ~ $ free
             total       used       free     shared    buffers     cached
Mem:       2041976   ** 1317948**     724028          0      28692     225996
-/+ buffers/cache:    **1063260**     978716
Swap:      4094972     338976    3755996

Adding Used and Buffered amounts to 2381208 which is 1.16 or 16% greater than physical RAM (at this moment).  So you could either apply a correction, or just be satisfied that you have filtered out the top RAM users and be happy.  Your script certainly satisfies the 80/20 rule:  80% of the problems are caused by 20% of the actors.  So as long as your script identifies those 20%, you can quickly remedy any situation.  Add a *wall* command to notify you when your php process exceeds some RAM and CPU level and you have a nifty Engine Warning Light.

---

### Post by proxess on 2014-01-15
The whole purpose of this command is to fetch the RAM usage per php-fpm profile, so we can reprimand the correct resource-hogging developers (possibly depriving them from their caffeine). We already have a warning light - SNMP. The command is to tell us who's at fault.

This is still enough to catch the culprit, but may not be enough to convince them they're in the wrong.

---

### Post by tgalati4 on 2014-01-15
If the coffee machine is hooked up to the internet, then that should be easy to do.  Perhaps a clever use of *pgrep* to find *php-fpm* piped to *pmap* and *vmstat* to find out which *php-fpm* instance is using up the most RAM.  Since you know (or suspect) that *php-fpm* is the bad actor, the script can be made much simpler.

---

