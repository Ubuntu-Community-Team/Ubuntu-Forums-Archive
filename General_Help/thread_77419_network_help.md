---
title: "network help"
date: 2005-10-16
forum: General Help
---

### Post by acejones on 2005-10-16
i've got eth0 setup correctly.  its activated.  my router sees it.  i can access my router.  i just can't get out.  konqueror gives me an Unknown host error.  not sure what to do next.

---

### Post by adwait on 2005-10-16
Maybe a DNS problem, check your /etc/resolv.conf file. Add the line
```
nameserver <router ip> 
``` 
to it. 
Or if you know the DNS servers add them directly:
```
nameserver <dns ip>
```

---

### Post by acejones on 2005-10-16
[QUOTE=adwait]Maybe a DNS problem, check your /etc/resolv.conf file. Add the line
```
nameserver <router ip> 
``` 
to it. 
Or if you know the DNS servers add them directly:
```
nameserver <dns ip>
```[/QUOTE]
i can't open the file.  when i do 
```
sudo kate /etc/resolv.conf
```
i get 
"kate: ERROR: Communication problem with kate, it probably crashed."

if i try as root, then it says
"kate: ERROR: KUniqueApplication: Can't determine DISPLAY. Aborting.

i even tried using openoffice writer, but it wouldn't let me due to rights restrictions.

---

### Post by Saarg on 2005-10-17
[QUOTE=acejones]i can't open the file.  when i do 
```
sudo kate /etc/resolv.conf
```
i get 
"kate: ERROR: Communication problem with kate, it probably crashed."

if i try as root, then it says
"kate: ERROR: KUniqueApplication: Can't determine DISPLAY. Aborting.

i even tried using openoffice writer, but it wouldn't let me due to rights restrictions.[/QUOTE]

Try this instead:
kdesu kate /etc/resolv.conf

---

### Post by knappen on 2005-10-17
I read somewhere that Kate and sudo don't really work. There is a bug apparently.

---

### Post by acejones on 2005-10-17
since this is a laptop, i brought it to work with me to see what would happen.  i actually got it to work by letting it use the dhcp server to get an address.  but it quit working again, giving me the same unknown host error.

---

### Post by adwait on 2005-10-17
That pretty much means its a DNS problem. Tey the solution I suggested.
```
sudo kwrite /etc/resolv.conf
```

---

### Post by acejones on 2005-10-17
actually, it started working.  i pulled the nic and put it back in and it connected.

---

