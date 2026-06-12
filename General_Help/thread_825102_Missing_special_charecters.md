---
title: "Missing special charecters"
date: 2008-06-10
forum: General Help
---

### Post by kunisch on 2008-06-10
Hello out there

I am i a bit of a problem.

Im currently running Ubuntu 08.04 on a laptop which has a Danish keyboard. In alln normal gnome programs i can write the characters: ^ | and ~. But in a few important programs: Maple and Matlab i can't write these the normal way (Alt Gr + char or shift char), i have to copy them.

I think this might be related to JAVA since matlab and maple both makes use of that.

So do any of you have any solutions?

Regards

---

### Post by ibuclaw on 2008-06-10
What exactly do you need the special characters for?
Are they essential to the programming language?
Which special characters are you trying to use?

Regards
Iain

---

### Post by kunisch on 2008-06-10
they are essential for doing any real math as well as any good programming in matlab.

the ones i need is: ^ ~ |

in matlab:

not equal ~=
or ||
a*a*a = a^3

so it is pretty important

---

### Post by ibuclaw on 2008-06-10
Ah, ok, the three most important ones then! :)

I think I've found a an old bug report that might be related to your issue [here.]("http://www.mathworks.com/support/bugreports/details.html?rp=357408")

Their fix for it is:
```
sudo chmod 000 /usr/share/fonts/truetype/ttf-gujarati-fonts/
```
and
```
sudo chmod 000 /usr/share/fonts/truetype/ttf-bengali-fonts/
```



[EDIT]
Also, a person with a Norwegian Keyboard fixed, again another very similar issue by setting 
```
Option                "XkbVariant"	"nodeadkeys"
```
In their /etc/X11/xorg.conf file under the section "InputDevice".
[Details here.]("http://ubuntuforums.org/showthread.php?t=142914")

Regards
Iain

---

### Post by kunisch on 2008-06-10
You my friend has just saved me.

thank you

the last hint was right, nodeadkeys indeed

---

### Post by baytuni on 2008-12-15
I am using Intrepid and there is no Input Device section in my xorg.conf and I have the same problem what should I do?

---

