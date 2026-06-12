---
title: "Copy or moving file"
date: 2018-06-08
forum: General Help
---

### Post by mlempenau on 2018-06-08
I am trying to copy a file to another location and at the same time give it a different name.  I get an error message saying I'm missing destination file operand.  

mlempenau@mlempenau1404:~$ sudo cp -i ~/Downloads/str-dfw301_a309973-active.ovpn/etc/openvpn/strongvpn.conf
[sudo] password for mlempenau: 
cp: missing destination file operand after ‘/home/mlempenau/Downloads/str-dfw301_a309973-active.ovpn/etc/openvpn/strongvpn.conf’
Try 'cp --help' for more information.
mlempenau@mlempenau1404:~$ 



What am I missing?  Thanks

---

### Post by sisco311 on 2018-06-08
A space between the source and destination:
```
cp -i ~/Downloads/str-dfw301_a309973-active.ovpn /etc/openvpn/strongvpn.conf
```

;)

---

### Post by mlempenau on 2018-06-08
The space was added and I get another error.  

mlempenau@mlempenau1404:~$ sudo cp -i ~/Downloads/str-dfw301_a309973-active.ovpn /etc/openvpn/strongvpn.conf
cp: cannot stat ‘/home/mlempenau/Downloads/str-dfw301_a309973-active.ovpn’: No such file or directory

I think I tried this yesterday ... I tried so many thing I can't remember!  :)

---

### Post by Holger_Gehrke on 2018-06-08
That error
> **mlempenau said:**
> 
cp: cannot stat ‘/home/mlempenau/Downloads/str-dfw301_a309973-active.ovpn’: No such file or directory


means that cp can't find the source file - you've either got a typo in there or you renamed or removed the file in your attempts to copy it. One way to reduce typos (and typing) in bash is to use command line completion. Type the first few letters and hit the tabulator key, the shell will complete the file or directory name as far as it can. If the shell finds more than one way to complete, it will complete to the point where the names differ. Hitting tab two more times in this situation makes the shell show the possible completions.

Holger

---

### Post by mlempenau on 2018-06-08
Excellent!  It worked.  Thanks.  :p

---

