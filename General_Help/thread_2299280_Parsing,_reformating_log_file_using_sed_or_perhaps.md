---
title: "Parsing, reformating log file using sed or perhaps a script?"
date: 2015-10-17
forum: General Help
---

### Post by lazerz on 2015-10-17
I have a file content as 
> 1.1.1.1 abcd
192.168.0.2 asdf.foobar.whatever

Originally the file was as :-

> bigspeedpro.com Intel:DOMAIN   from [http://malc0de.com/bl/BOOT](http://malc0de.com/bl/BOOT) via intel.criticalstack.com     F
1.1.1.1 Intel:DOMAIN   from [http://abcd.com/bl/BOOT](http://abcd.com/bl/BOOT) via intel.criticalstack.com     F

Using script below, I reduced to lines shown (at start)

> #!/usr/bin/awk -f

/^[[:digit:]]*\.[[:digit:]]*\.[[:digit:]]*\.[[:digit:]]*/ { 
printf $1; 

gsub (/http\:\/\//," "); 
gsub (/https\:\/\//," "); 
gsub(/\.com/," ");
printf " "$4"\n";
}

Now, I'm bothered about "asdf.foobar.whatever" these long domains I want to shorten to string i already know what to replace with. For after IP address
I want If the domain name matches any string e.g abcd then replace entire string domain name with the matched word. i.e abcd. How can it be done?

---

### Post by TheFu on 2015-10-17
I'm confused.

The "before" and "after" don't make sense to me. Expected:
```
bigspeedpro.com malc0de.com
1.1.1.1 abcd.com
```
from the input. Perhaps a clearer relationship explanation would help? 

I can't help with awk. I'd use something like: ```
awk ‘{print $1,$4}’ file.log
``` to get started.

If that is important, would be good if awk was in the thread title. I'd use **perl** myself or a simple **cut** to get the 1 fields you want. Perl has the split() function.

Do you just want to make a hosts file from existing logs? Perhaps there is a better solution to what you are trying to accomplish in this step?

---

