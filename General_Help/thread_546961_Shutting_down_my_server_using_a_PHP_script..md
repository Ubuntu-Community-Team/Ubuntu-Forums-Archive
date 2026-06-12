---
title: "Shutting down my server using a PHP script."
date: 2007-09-09
forum: General Help
---

### Post by climbjm on 2007-09-09
I want to shut down my server using a PHP script (or a bash script being executed some way via apache).

I have a server in my room that is really loud... and well the wife doesn't like sleeping with it on (and I don't blame her).  However, when I am gone, I would like her to be able to just click a link and shut it down, rather than having to log in via SSH and send it commands.  Yet I also don't want her to just unplug it.  So I am trying to make this as easy as possible.

I tried this using PHP, but no go.  Any ideas?

```
shell_exec('shutdown');
```

I've already tried halt, reboot, poweroff with the functions shell_exec(), exec(), and system().
Do you think it is a permissions thing?

I would try sending it "sudo shutdown" but I dont know how to send it the password it asks for.

Thoughts?

Side Note: I posted this on PHPfreaks.com but it seems as if no one knows there either.  Here is the URL anyway. [http://www.phpfreaks.com/forums/index.php/topic,158691.0.html](http://www.phpfreaks.com/forums/index.php/topic,158691.0.html)

---

### Post by ghantoos on 2007-09-09
apache server runs under "apache" user and group.

You can check out conf file in /etc/apache.

This user doesn't have any system privileges.

You can try and give it more privileges, but it is not recommended, specially if your server is accessible from the internet.

cheers,

ghantoos

---

### Post by ansi on 2007-09-09
Hello,

> **climbjm said:**
> 
I would try sending it "sudo shutdown" but I dont know how to send it the password it asks for.



You could configure your sudo to run some specified commands without password asking.

Quote from sudoers' man page (*man sudoers*):
> 
       For example:

```
        ray    rushmore = NOPASSWD: /bin/kill, /bin/ls, /usr/bin/lprm
```

       would allow the user ray to run /bin/kill, /bin/ls, and /usr/bin/lprm
       as root on the machine rushmore as root without authenticating himself.



Good luck ;),

---

### Post by climbjm on 2007-09-09
> **ansi said:**
> 
You could configure your sudo to run some specified commands without password asking


Where do I edit/configure my "sudo"?

Looks just like what I want.
So I would do something like...

```
        user    machine = NOPASSWD: /sbin/halt
```

---

### Post by ansi on 2007-09-09
> **climbjm said:**
> Where do I edit/configure my "sudo"?

Looks just like what I want.
So I would do something like...

```
        user    machine = NOPASSWD: /sbin/halt
```


I think execution of this command should help :).
```
sudo visudo
```

I hope you understand you should replace "*user*" and "*machine*" with actual values.

---

