---
title: "IEs 4 Linux - Installation Problem"
date: 2008-03-13
forum: General Help
---

### Post by madkid on 2008-03-13
I have tried to install IEs 4 Linux on Ubuntu 7.04. The first file that it tries downloading will get up to 10% or so before it says that the file was corrupted. I tried it again and it picked up from the 10% and continued on until it hit 15% and gave me the same file corruption error. I'm not at home right now so I don't have all the information on the error message so if it is needed, I'll get it when I get home. Any help would be appreciated. Thanks.

---

### Post by CadetD on 2008-03-13
Are you talking about Internet Explorer 4? How are your downloading this?

---

### Post by Kerry_W on 2008-03-13
i just grabbed it very quickly without any problems with the command:
```
wget http://www.tatanka.com.br/ies4linux/downloads/ies4linux-latest.tar.gz
```


found on this site: [http://www.tatanka.com.br/ies4linux/page/Installation:Ubuntu](http://www.tatanka.com.br/ies4linux/page/Installation:Ubuntu)

or try a direct download from here: [http://www.tatanka.com.br/ies4linux/download.html](http://www.tatanka.com.br/ies4linux/download.html)

---

### Post by madkid on 2008-03-13
CadetD: I'm not download Internet Explorer 4. I'm downloading IE 6 using IEs 4 Linux. Besides, why would I want IE4?

Kerry_W, I already have the installation script downloaded. Here's the error I get while trying to install any version of IE:

 49%  DCOM98.EXE!! An error ocurred when downloading. Please run IEs4Linux again. Corrupted file: DCOM98.EXE


I've already retried a few times already. That's all I get. I managed to install it with the IEs4Linux script with a different Linux distro and it worked like a charm. What's wrong with this one? Thanks.

---

### Post by sarracenia on 2008-03-13
I am trying to install this as well, and get a similar error message:

71%  IE_S5.CAB!! An error ocurred when downloading. Please run IEs4Linux again. Corrupted file: ie6/EN-US/IE_S5.CAB.

(sorry for the thread hijack ... but I thought it might be related)

---

### Post by madkid on 2008-03-14
It probably is related.

---

### Post by namegame on 2008-03-14
The install process seems extremely buggy to me. I have successfully installed it, however, I had to re-run the installation several times before it was completely successful.

---

### Post by Fatman_UK on 2008-05-15
Same here. Could be a custom downloader issue? IEs4Linux is a shell script so I'll take a look.

...

It's using standard download commands, so it's not a custom downloader problem. From lib/functions.sh:

```

if [ "$HASWGET" = "1" ]; then
   pid=$(wget -q -b -t 1 -T 5 -U "$useragent" -o /dev/null $URL $WGETFLAGS -O "$file" | sed -e 's/[^0-9]//g')
elif [ "$HASCURL" = "1" ]; then
   ( curl -s -A "$useragent" "$URL" -o "$file" & )
   pid="$(pidof curl)"

```

(While I was writing this it finished the download cycle and installed the IEs without further problems. It's a good thing the script supports resuming, otherwise it'd never have installed anything.)

---

