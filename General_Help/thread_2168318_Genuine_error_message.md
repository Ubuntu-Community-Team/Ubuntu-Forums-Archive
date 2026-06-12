---
title: "Genuine error message"
date: 2013-08-17
forum: General Help
---

### Post by kkelly77 on 2013-08-17
I've gotten the following error message on my version of 12.04 LTS

[IMG]http://i43.tinypic.com/2zji174.jpg[/IMG]

The message doesn't give me an option for more details or what is actual causing the problem. Can anyone help with identifying the error message? Thanks.

---

### Post by tgalati4 on 2013-08-17
Report the problem then look in /var/log/apport for messages.

---

### Post by ibjsb4 on 2013-08-17
If you do not find anything in the logs and your system is running fine, then you can just disable the ["apport"]("http://ubuntuforums.org/showthread.php?t=2053494&p=12219467&viewfull=1#post12219467") reporting system.  Its suppose to be [disabled by default]("https://wiki.ubuntu.com/Apport#Why_is_it_disabled.3F").  It is not installed on my system by choice.

[More reading on apport]("http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=apport+bugs&sa=Search&cof=FORID:9")

---

### Post by kkelly77 on 2013-08-17
Thanks for the replies guys.

Reading how to disable 

> **Ubuntu 12.04 and later**

 Starting with 12.04, Apport itself is running at all times because it collects crash data for whoopsie (see [ErrorTracker]("https://wiki.ubuntu.com/ErrorTracker")). However, the crash interception component is still disabled. To enable it permanently, do: 
sudo nano /etc/apport/crashdb.conf... and **add a hash symbol # in the beginning** of the following line: 
        'problem_types': ['Bug', 'Package'],To disable crash reporting just remove the hash symbol.

I've checked crashdb.conf and there is no hash tag on the beginning of the line 
'problem_types': ['Bug', 'Package'],

So should I be getting these error messages?

---

