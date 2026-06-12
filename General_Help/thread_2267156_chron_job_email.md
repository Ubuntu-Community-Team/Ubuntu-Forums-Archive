---
title: "chron job email"
date: 2015-02-27
forum: General Help
---

### Post by aaron50 on 2015-02-27
Hello everyone,

I am very new to bash scripting and cronjobs. I have this script that is stored at /home/aaron50/bin/ and is called my_script

```
#!/bin/bash
HDDS="/dev/sda"
HDT=/usr/sbin/hddtemp
ALERT_LEVEL=55
for disk in $HDDS
do
  if [ -b $disk ]; then
        HDTEMP=$(sudo $HDT $disk | awk '{ print $4}' | awk -F '°' '{ print $1}')
        if [ $HDTEMP -ge $ALERT_LEVEL ]; then
           echo | mutt -s "System going down as hard disk : $disk temperature $HDTEMP°C crossed its limit" emailaddress@gmail.com
        else
           echo | mutt -s "System Temperature : $HDTEMP°C all is good" emailaddress@gmail.com
        fi
  fi
done

```

I have added the path to my $PATH with
```
export PATH=$PATH:/home/aaron50/bin/
```

this allows me to run my script from the command line with
```
my_script
```

The script works perfect and is sending me an email with the temperature. when i put this into a cron job however it is not working as intended. I think i know why but i am not experienced enough to know how fix it, so any help is greatly appretiated. Here is what i have done with my cron job
```
crontab -e
```
```
*/10 * * * * /home/aaron50/bin/my_script
```

This does send me an email on the 10th minute of the hour, but it does not put the temperature in the email. it just says "System Temperature °C all is good". I think it is because i am using sudo in the script (line 8) to access the hddtemp. I tried putting this into my "sudo crontab -e" file, but it did not do anything there, it didn't even send me an email. Do i need to change my cronjob or my script?

---

### Post by ian-weisser on 2015-02-27
> **aaron50 said:**
> Do i need to change my cronjob or my script?

Both, I think.

You are trying to do two separate tasks.

One task (reading the HDD temp) requires root.
The other task (sending an e-mail) does not require root.

I would put each task into a separate script....I try to avoid mixing permissions. It also makes troubleshooting easy.

Your cronjob must run as root, and calls a root script that, in turn, calls the two subordinate scripts using the appropriate permission. Here's an example:
```
#!/bin/sh

## Check the HDD temp, and save the value in /tmp
/usr/local/monitor_temperature.sh

## Read the value from /tmp and email it
sudo --user=aaron /usr/local/temperature_email.sh 

```


Of course, the way *I* would do it might seem obtuse or silly to you. The set containing possible right answers is enormous.

---

### Post by aaron50 on 2015-02-27
> **ian-weisser said:**
> 
Of course, the way *I* would do it might seem obtuse or silly to you.

ian, nothing is obtuse. I am learning all of this, including linux, so setting up a file structure and script structure is part of that. Unfortunately, you are dealing with a newbie, and had a hard time writing even this script (a lot of grabbing different things online), i was so excited when i got this to run from the command line. One thing i am a little concerned about with your method, correct me if i am wrong, but each time the cron runs it will input the temp into a text file. Won't this text file eventually have a bunch of temperatures in it, therefore emailing me a bunch of temperatures instead of the one that was just measured?

Without sounding too needy, is there anyway you could help me set this up?

Thanks for your help.

---

### Post by ian-weisser on 2015-02-27
> **aaron50 said:**
> Won't this text file eventually have a bunch of temperatures in it, therefore emailing me a bunch of temperatures instead of the one that was just measured?

Try it.
```
$ echo date > /tmp/tempfile     ## '>' means overwite the existing file, if any
$ echo date >> /tmp/tempfile    ## '>>' means append to the existing file, if any
```

Now you know how to prevent endlessly-growing files.

You don't need much help,
Start with a root script that reliably reads the HDD temp, and saves that value in a world-readable location (echo $TEMP > /tmp/hdd_$HDD_temp). You already have 95% of it written above.

---

### Post by kjohri on 2015-02-27
It is better to avoid the suffix ".sh" in the script file name and let the file name comprise of only lowercase characters and digits. Look at this link, [anacron]("http://www.softprayog.in/tutorials/anacron").

---

### Post by nerdtron on 2015-02-27
better to use /bin/bash /path/to/my/script.sh rather than just the script name itself. In ubuntu, cron default uses sh shell, but your script is written for bash shell so you should explicitly provide the shell you want to use.

---

