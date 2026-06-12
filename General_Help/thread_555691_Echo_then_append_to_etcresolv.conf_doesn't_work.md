---
title: "Echo then append to /etc/resolv.conf doesn't work"
date: 2007-09-20
forum: General Help
---

### Post by Lumbee1 on 2007-09-20
I cannot seem to echo information and append it to my /etc/resolv.conf file.  

user@Thinkpad:~$ sudo echo "nameserver 10.0.0.255" >> /etc/resolv.conf
bash: /etc/resolv.conf: Permission denied
user@Thinkpad:~$

But I can make is work if I switch to superuser and run the same command.

user@Thinkpad:~$ su
Password: 
root@Thinkpad:/home/user# echo "nameserver 10.0.0.255" >> /etc/resolv.conf
root@Thinkpad:/home/user# 

This same command has worked previously with sudo and has even worked after doing it manually through su.

What gives?

---

### Post by tszanon on 2007-09-20
> **Lumbee1 said:**
> I cannot seem to echo information and append it to my /etc/resolv.conf file.  

user@Thinkpad:~$ sudo echo "nameserver 10.0.0.255" >> /etc/resolv.conf
bash: /etc/resolv.conf: Permission denied
user@Thinkpad:~$

But I can make is work if I switch to superuser and run the same command.

user@Thinkpad:~$ su
Password: 
root@Thinkpad:/home/user# echo "nameserver 10.0.0.255" >> /etc/resolv.conf
root@Thinkpad:/home/user# 

This same command has worked previously with sudo and has even worked after doing it manually through su.

What gives?
I once tried using >> to append to some file. At that time, I thought it didn't work because the write operation was being performed with my user permissions. I never succeeded doing this without switching to root before. Are you sure that, when it worked, you didn't have write access to /etc/resolv.conf?

---

### Post by bodhi.zazen on 2007-09-20
Yea, you need to change the format of your comand :

```
sudo sh -c "echo "nameserver 10.0.0.255" >> /etc/resolv.conf"
```

---

### Post by tszanon on 2007-09-20
> **bodhi.zazen said:**
> Yea, you need to change the format of your comand :

```
sudo sh -c "echo "nameserver 10.0.0.255" >> /etc/resolv.conf"
```
I can't test it now, but are you sure that the quotation marks wouldn't conflict with each other? Like, the second mark being considered the closing mark of the first, then the word nameserver being considered a syntax error or something else?

---

### Post by Wolki on 2007-09-20
That doesn't seem to work here. I can do it with tee, though:

```
echo "nameserver 10.0.0.255" | sudo tee -a /etc/resolv.conf
```

---

### Post by Lumbee1 on 2007-09-20
For some odd reason, it started working :confused: but now I can't rewrite resolve.conf to restore the original settings.

Connect script (add a # to all previous lines and appends search and nameserver)
if ! grep 'search 10.0.0.255' /etc/resolv.conf > /dev/null; then
        sed 's/^\(.\)/#\1/' /etc/resolv.conf
        echo "search raleigh.com" >> /etc/resolv.conf
        echo "nameserver 10.0.0.255" >> /etc/resolv.conf
fi


Disconnect script (removes search and nameserver and # before original lines)
if grep '10.0.0.255' /etc/resolv.conf > /dev/null; then
        grep -v "search raleigh.com" /etc/resolv.conf > /etc/resolv.conf.new
        grep -v "nameserver 10.0.0.255" /etc/resolv.conf.new > /etc/resolv.conf
        sed -ie 's/^#//' /etc/resolv.conf
fi

Since typing this, the disconnect script works but the connect script doesn't.  This is really weird and the results change each time.

---

