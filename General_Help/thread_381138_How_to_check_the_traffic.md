---
title: "How to check the traffic"
date: 2007-03-10
forum: General Help
---

### Post by jmvidalvia on 2007-03-10
I am using wvdial with huawei E220.
As I have a maximum amount of traffic per month of 1 Gb I would like to checK how many bytes I downloaded every session, or day, or month.
Any idea?
Many thanks!

---

### Post by schilcha on 2007-03-10
Hi, I don't know any out-of-the-box solution to your problem, but here's a simple home-made approach:
```

cat /proc/net/dev | grep eth0 | tr ":" " " | tr -s " " |cut -d' ' -f2,3,11

```
This retrieves the traffic statistics for interface eth0 (should be something like ppp0 for you) and returns 3 space-separated columns containing the interface-name, the received bytes and the sent bytes.

Just put this in a script and add it as pre-down command to your /etc/network/interfaces-file for your modem-connection. Append the output to some file and you can do with the numbers whatever you like.

Hope that helped!

---

### Post by jmvidalvia on 2007-03-10
Thank you very much.
Menwhile I learned I can get that as well with:
cat | grep from /var/log/messages
and send the output to a file.
I understand I can add for every session the total data traffic.
Now the question is: I have a file with different rows with data.
¿**how can I make some calculation with those figures**? like adding the total amount and so on...
Thank you very much!

---

### Post by schilcha on 2007-03-10
I once wrote a perl-cgi-script that read such a file (with one row for each session) and wrote the monthly sums to html-output. However, this script was for monitoring vpn-traffic for approx. 20 different clients. It might be a little overkill for your situation. 

If you do not fancy perl (or any other scripting language), here's again a quick approach:
```

total=0
for part in `cat volume.log`; do let "total+=part"; done
let "total/=(1024*1024)"
echo "Total volume summed from forl volume.log is $total MB"

```
This will go through all numbers in the file volume.log and sum them up. Afterwards, the sum is divided by (1024*1024) to convert it to MBytes (integer division only!).

If you have several columns in the file, use cut instead of cat to separate those columns you want to be summed.

---

### Post by jmvidalvia on 2007-03-10
Thank you very much.
I assume I can copy-paste this text to a script and execute it.
Just one question: when you mention 'cat volume.log', is *volume.log* supposed to be the name of the file where I sent the rows with traffic?
Thanks again!

---

### Post by schilcha on 2007-03-10
Yes to all of your questions above.

Make sure to use bash (dash), since the loop-syntax and the let-command are bash-specific. 

Good Luck!

---

### Post by jmvidalvia on 2007-03-11
Seems to be a problem.
My volume.log looks like:

ppp0 249454 113529
ppp0 274953 152168

I created a script like:

#/bin/sh
total=0
for part in `cat volume.log`
do let "total+=part"
done
let "total/=(1024*1024)"
echo "Total volume summed from for volume.log is $total MB"

But shows:
Total volume summed from for volume.log is 0 MB

Thank you very much for your help!

---

### Post by schilcha on 2007-03-11
I just tried it with your input:
One problem is your first line, which should read "#!/bin/bash", since the command let seems to be unknown to sh. 

0 is returned, since "let" does not return decimal places and your traffic is smaller than 1MB (0.8MB, which is truncated to 0 by let).

---

### Post by schilcha on 2007-03-11
Couldn't keep my fingers off of it. Having this plain integer-divisions is not satisfying. I don't know how to do float-arithmetics in bash, so I usually use dc (a RPN-command-line calculator -- I hope it's installed by default). So here's what'll give you two digits after the decimal point:
```

#!/bin/bash

# set dc's precision and push 0 to dc's stack
echo -e "2\nk\n0" > /tmp/_tmp.vol

for part in `cat volume.log`; do 
  # if we're dealing with a number, push and add in dc
  [[ $part =~ "[^0-9]" ]] || echo "${part}+" >> /tmp/_tmp.vol
done
# divide by 1024*1024 and print result in dc
echo -e "1024/\n1024/\np" >> /tmp/_tmp.vol

# finally, do the calculation in dc and save the output
total=`dc < /tmp/_tmp.vol`

# clean up...
/bin/rm /tmp/_tmp.vol

# say, what has to be said
echo "Total volume summed from for volume.log is $total MB"

```

Good Luck!

---

### Post by jmvidalvia on 2007-03-11
Hey! Super -great!
I changed sh by bash and my (your) first script worked fine.
But now, the second one, is even better, perfect!
Thank you very much for your help and your nice work.

---

