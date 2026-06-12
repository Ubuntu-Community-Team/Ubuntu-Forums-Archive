---
title: "FTP script  and a question about a wiki"
date: 2007-06-21
forum: General Help
---

### Post by JermainWijnhard on 2007-06-21
Could someone help me with this code? I can't figure out what im doing wrong ><

I want to use a script to upload some stuff for me and came up with this:

```
#!/bin/bash


filename="/home/jermain/scrout/sysreport.html"

hostname="ftp.something.com"

username="user"

password="something"

ftp -vin $hostname <<EOF

quote USER $username

quote PASS $password



binary

cd /HTML
put $filename


quit

EOF
```

But it won't upload the file:

```
Connected to ftp.something.com.
220 ProFTPD 1.2.10 Server ready.
Remote system type is UNIX.
Using binary mode to transfer files.
331 Password required for user
230 User user logged in.
200 Type set to I
250 CWD command successful
local: /home/jermain/scrout/sysreport.html remote: /home/jermain/scrout/sysreport.html
200 PORT command successful
550 /home/jermain/scrout/sysreport.html: No such file or directory
221 Goodbye.
```

i think the problem is that the server doesn't have the same directories as my client does but i wouldn't know what to do about that.

Also I was wondering, is there a wiki out there where people can search, place and adjust unix scripts? I've been playing with the idea but lack the skills / resources to set something like that up. So i'm kinda hoping im not the first to have thought of it.

Anyone and everyone thanks for helping / reading.

---

### Post by Brucevdk on 2007-06-22
> **JermainWijnhard said:**
> i think the problem is that the server doesn't have the same directories as my client does but i wouldn't know what to do about that.

It seems you're correct, how about using: *put local-file [remote-file]*?
```

put /home/jermain/scrout/sysreport.html sysreport.html

```

Which reminds me I personally have a script laying around which uses lftp to mirror a directory and its contents.
```

lftp -u $username,$password $host << EOT
cd projects
mirror -R $local_directory .
EOT

```

> **JermainWijnhard said:**
> Also I was wondering, is there a wiki out there where people can search, place and adjust unix scripts? I've been playing with the idea but lack the skills / resources to set something like that up. So i'm kinda hoping im not the first to have thought of it.

You might be interested in [DocForge]("http://docforge.com/wiki/Main_Page"), at the moment it doesn't seem to be booming with activity but it could become what you're talking about.

---

