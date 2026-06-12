---
title: "What is wrong with my wget statement?"
date: 2007-11-07
forum: General Help
---

### Post by MCMcButtah on 2007-11-07
I am trying to grab the amazing desktop wallpaper off of [www.interfacelift.com](www.interfacelift.com). Being lazy, I do not feel like clicking 2,000 links just to get the pics so I have been trying to harvest them using wget which is not working as I would expect. Here is the statement I am using

wget -r -l2 -nd -A.jpg -erobots=off -proxy=on [http://interfacelift.com/wallpaper/index.php?w=1920&h=1200&sort=date&id=&page=2](http://interfacelift.com/wallpaper/index.php?w=1920&h=1200&sort=date&id=&page=2)

Now if you check out that URL you will see a page with some preview pics and then next to each is a link titled download which links to pictures stored like this:

[http://interfacelift.com/wallpaper/downloads/01413_seaofsand_1920x1200.jpg](http://interfacelift.com/wallpaper/downloads/01413_seaofsand_1920x1200.jpg)

Now I would think because I am using the recursive -r arguement it should at least grab all the jpg files that are directly linked on that page. However, the only thing it will download are the preview pictures which have a resolution of like 500px not the 1920x1200 ones I am looking to grab.

wget does work if I specify the file directly such as

wget [http://interfacelift.com/wallpaper/downloads/01413_seaofsand_1920x1200.jpg](http://interfacelift.com/wallpaper/downloads/01413_seaofsand_1920x1200.jpg)

But that isn't useful as it only grabs 1 file, I need it to recursively grab at least all the high res pics linked off the page.

Anyone have a clue why this might not be working? Thanks.

---

### Post by p_quarles on 2007-11-08
The first command is downloading a PHP script. That's why you're getting that page instead of the actual image files it links to. 

This should work (it did for me, anyway)
```
wget -r -nd -l2 -A1920x1200.jpg -erobots=off -w 8 http://interfacelift.com/wallpaper/ 
```
The "-w 8" option sets an 8 second pause between each file, which will reduce the load on the server and the chances that your IP will get banned by an annoyed admin. :)

---

### Post by hero3616 on 2007-11-10
Hi,

Suggested wget commands will not work. Unfortunately it's not that simple. Here is a script that should do what you want (many thanks go to K. Cem Karadeniz). It's a modified version from [http://vpol.livejournal.com/121940.html](http://vpol.livejournal.com/121940.html).

Use Gentoo for better community support when it comes to scripting.

#!/bin/bash
# usage: ./getwallpapers.sh 1600 1200
# usage: ./getwallpapers.sh 2560 1600 etc.

if [ $# != 2 ]; then
	echo "usage: `basename $0` width height";
	echo "i.e. : `basename $0` 1400 1050";
	exit 0;
fi

PAGEID=1
PAGEMAX=`wget http://interfacelift.com/wallpaper/index.php?sort=date\&w=${1}\&h=${2} -O - 2> /dev/null | grep -B 1 "next page"|grep -v "next page"|cut -d '=' -f 8|cut -d \" -f 1`
echo "PAGEMAX=$PAGEMAX (there will be `expr $PAGEMAX \* 10` files max)"
echo "Please wait (a long time)..."
fcount=0

while true; do
	for LINK in `wget http://interfacelift.com/wallpaper/index.php?w=${1}\&h=${2}\&sort=date\&id=\&page=${PAGEID} -O - 2> /dev/null | grep "${1}x${2}.jpg"|cut -d \" -f 4`; do
		if [ -f "`basename $LINK`" ]; then
		:
		else
			let fcount++
			echo "`basename $LINK` ($fcount)"
			wget -w 2 --user-agent="Opera" http://interfacelift.com${LINK} 2> /dev/null
		fi
	done
	if [ ${PAGEID} -eq ${PAGEMAX} ]; then
		exit 0
	fi
	let PAGEID++
done

Thanks,

---

### Post by MCMcButtah on 2007-11-11
Thank you both for trying to help. So far I have not been able to get this to work.

hero3616 I tried the script and get the following errow\r, do you have any ideas?

berryberry@shiraz:~/Desktop/try/try2$ sh getwallpapers.sh 1920 1200
--18:27:07--  [http://interfacelift.com/wallpaper/index.php?sort=](http://interfacelift.com/wallpaper/index.php?sort=)
           => `index.php?sort=.8'
Resolving interfacelift.com... 209.85.64.50
Connecting to interfacelift.com|209.85.64.50|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/html]

    [  <=>                                ] 53,412       190.29K/s

18:27:08 (189.77 KB/s) - `index.php?sort=.8' saved [53412]

Usage: grep [OPTION]... PATTERN [FILE]...
Try `grep --help' for more information.
getwallpapers.sh: line 17: next page: command not found
expr: syntax error
PAGEMAX= (there will be  files max)
Please wait (a long time)...
getwallpapers.sh: line 29: syntax error near unexpected token `newline'
getwallpapers.sh: line 29: `wget -w 2 --user-agent="Opera" http://interfacelift.com${LINK} 2> '
berryberry@shiraz:~/Desktop/try/try2$ 

Does it have something to do with my shell? I tried at the prompt /bin/bash getwallpapers.sh 1920 1200 as well but that did not seem to make a difference. Thanks again

---

### Post by hero3616 on 2007-11-12
MCMcButtah,

Please make sure quotation marks are copied / pasted correctly. Especially "`" character (the key under the escape key on keyboard). After saving and making it executable (chmod 755) run it:

$ ./getwallpapers.sh 1600 1200

If it still doesn't work (after making sure everything copied/pasted correctly) please use the file attached to this message. It's the exact file that I downloaded 2560x1600 1600x1200 1024x768 files (it's exactly the same code that I put here).

Thanks

---

### Post by MCMcButtah on 2007-11-12
The attached file worked great. Thank you very much for taking the time to help me with this.

---

