---
title: "using Cron.daily problem"
date: 2008-06-05
forum: General Help
---

### Post by wgregori on 2008-06-05
I've placed this command in cron.daily

/usr/sbin/ntpdate ntp.ubuntu.com pool.ntp.org

This command works if I login and execute as root.  However, I get the following error message emailed to me daily.

/etc/cron.daily/ntpdate:
run-parts: failed to exec /etc/cron.daily/ntpdate: Exec format error
run-parts: /etc/cron.daily/ntpdate exited with return code 1

Any ideas what I'm doing wrong?

Thanks,
Wayne

---

### Post by HermanAB on 2008-06-05
The most like problem is that you neglected to specify the full path to *everything* in the cron script, so it cannot find something.  The cron environment is very limited, for security reasons.

---

### Post by wgregori on 2008-06-05
Thanks

---

### Post by banuk77 on 2011-07-04
It may be too late to reply, but not for someone like me who spend a lot of time scraching and searching why my script only not working.

The problem i had was, I forgot the Shebang:( , Some small mistake took days of searching

```
[COLOR="Blue"]#!/bin/sh[/COLOR]
```

So.. for this type of error i will first check this line to be at the first line of the script file.

---

### Post by Tom 6 on 2011-11-10
Hi :)
In the guide

[https://help.ubuntu.com/community/UbuntuTime#Command_Line_ntpd](https://help.ubuntu.com/community/UbuntuTime#Command_Line_ntpd)

it showed 

{{

# 
#!/bin/sh
ntpdate ntp.ubuntu.com

}}

but shouldn't it be 

{{
!/bin/sh
ntpdate ntp.ubuntu.com
}}
??
Arrrgh.  Please help as i don't want the page to give wrong advice!
Regards from
Tom :)

---

### Post by luckyEddy on 2012-01-26
> #!/bin/sh Indicates the shell to use. It is correct this way.

---

### Post by Tom 6 on 2012-01-26
HI :)
Good :)  Ok, so it is right on the page now then :)
Thanks and regards from
Tom :)

---

