---
title: "shell script failing first line"
date: 2015-01-11
forum: General Help
---

### Post by jimbo10 on 2015-01-11
just wrote this shell script to select from a doz' or so options to connect to a VPN....

but.....the first line fails...

general "algorithm" is:

cd VPN_dir
echo "select an option"
echo options 1-13
read SELECTION
case $SELECTION in
<options 1-13> ....... sudo <execute vpn option>
exit 1
esac

dunno if the actual code in the 'case' is wrong or not.......because it doesn't even change to the dir  (cd VPN_dir) .... i wrote a separate little script with just cd VPN_dir in it and.....nothing!....stayed in the home dir...........
(the echo options appear on screen OK.......and await an input from the command line.....)

here is the actual error msg......

/usr/local/bin/blckr: line 27: syntax error near unexpected token `)'
/usr/local/bin/blckr: line 27: `2) echo "Estonia...."'

("blckr" is the file name.....i used +chmod to make it exe ...... [then mv to /usr/local/bin] Estonia is one of the vpn locations)

but.......like i said....it doesn't change the dir......
also tried......  cd [FONT=arial]~/vpn_dir .........no difference......

[SIZE=2]any help much appreciated......thnx!   [/SIZE]
[/FONT]

---

### Post by Vaphell on 2015-01-11
asking about syntax error and not showing any code is weird to say the least. I'll make a guess though - you didn't terminate individual case blocks with ;;

---

### Post by jimbo10 on 2015-01-11
> **Vaphell said:**
> asking about syntax error and not showing any code is weird to say the least. I'll make a guess though - you didn't terminate individual case blocks with ;;


sorry....what happened was i didn't make a 'back up' of the sh script....so.....of course.....when i made it exe.....it was gone.....
the algorithm was the best i could do......  :(

its in the bash shell.......when you say *didn't terminate individual case blocks with ;; .......*that sounds like it should'v been in the c shell (?)
(maybe i should'v just used if....else if         [?]    )

but ....like i said....it didn't even xct the first line properly.....didn't change the dir....

i just tried writing this....


cat >blck_bck
cd ~/vpn_dir
sleep 5
ls
^d

it displayed the vpn_dir OK......but......when i tapped in "pwd".....i was back in me home dir......

what gives   :confused:

(as always: any help [COLOR=#0000ff]***much***[/COLOR] appreciated......ta!)

*edit*
OK.......am reading the BASH 'guide'......might pick up some-thing there, eh?!? ........cheers!

---

### Post by nerdtron on 2015-01-11
Scripts run on their own terminal (or console) therefore, if you script has command "cd /path/here" but you are currently in the /home/username/ and you run the script, your directory won't change (although the script ran successfully and it did changed it's directory) 

Tips for running bash scripts:
Even if your script is not executable, you can run it as:
```
bash /my/script.sh
```

If you want to see what is running line by line on your script, you can try:
```
bash -x /my/script.sh
```

---

### Post by steeldriver on 2015-01-11
> **jimbo10 said:**
> sorry....what happened was i didn't make a 'back up' of the sh script....so.....of course.....when i made it exe.....it was gone.....

A  file shouldn't "go" anywhere when you make it executable - you should still be able to open it from a text editor, or display it in the terminal using the "cat" command

---

