---
title: "Installing VPN on Ubuntu 10.12"
date: 2013-01-12
forum: General Help
---

### Post by berry1 on 2013-01-12
[SIZE=4]Hi everyone :)

Noob to Ubuntu here, just reformatted and installed Ubuntu 12.10 today so still moving things round and getting used to the commands. Now the problem is that im trying to install my Private Internet Access VPN but [SIZE=4]a[SIZE=4]re[/SIZE][/SIZE] having problems moving a file around. A file called *ca.crt* *has to be moved to *[I]/etc/openvpn[SIZE=4] .

[SIZE=4]T[SIZE=4]he [SIZE=4]c[SIZE=4]om[SIZE=4]mand i [SIZE=4]attempted to move the file with was [/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/I][/SIZE][FONT=Book Antiqua][SIZE=4][COLOR=#000000]
mv [/COLOR][COLOR=#000000]ca.crt[/COLOR][COLOR=#000000] ~/[/COLOR][COLOR=#000000]ect[/COLOR][COLOR=#000000]/[/COLOR][COLOR=#000000]openvpn[/COLOR][COLOR=#000000]/

[SIZE=4]And all i keep getting back i[SIZE=4]s [SIZE=4]No such file or directory. 

[SIZE=4]If someone [SIZE=4]could advise me on how i can move this [SIZE=4]file
[SIZE=4][SIZE=4]i[SIZE=4]t [SIZE=4]would be appreciated.

[SIZE=4]T[SIZE=4]hanks :)[/SIZE][/SIZE]
[/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/COLOR][/SIZE][/FONT]

---

### Post by Cheesemill on 2013-01-12
I think you mean 12.10, there is no such thing as Ubuntu 10.12.

Where is the ca.crt file at the moment?
Assuming it is in your Downloads directory the correct command would be...
```
sudo mv ~/Downloads/ca.crt /etc/openvpn/
```

---

