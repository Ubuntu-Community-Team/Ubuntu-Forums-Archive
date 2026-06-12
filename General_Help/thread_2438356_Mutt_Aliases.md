---
title: "Mutt Aliases"
date: 2020-03-10
forum: General Help
---

### Post by zerubbabel on 2020-03-10
Is it possible to reference a Mutt alias on the Mutt command line?

What I'm trying to do is make a simple script that enables me to send a one-line email from the Mutt command line to a recipient for whom I have defined an alias. I want the script to simply accept two arguments on the command line: the alias of the recipient and a quoted string which is the message to send. Any suggestions will be much appreicated.

---

### Post by zerubbabel on 2020-03-11
Turned out to be trivially easy. Don't know how I missed the "-A" command line option. Here is the working script:

#!/bin/sh

# Syntax: ./sms alias "message"

ADDRESS=`mutt -A $1`
echo $2 > sms.txt
mutt -s "SMS" $ADDRESS < sms.txt

---

### Post by EuclideanCoffee on 2020-03-11
Awesome! Please edit topic with [Solved] to help others.

---

