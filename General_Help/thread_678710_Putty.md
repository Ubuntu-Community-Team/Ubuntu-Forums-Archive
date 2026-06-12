---
title: "Putty"
date: 2008-01-26
forum: General Help
---

### Post by taimur on 2008-01-26
hi i m using my server remotly by putty through ssh the problem i m running two type of applications on it 

one is like this there is a command to run the application and suppose if i close my putty the program don't stop it is working internally and if i want to stop the progarm i have to use killall to stop the program 
this is ok i want it like that

and the other apllication is not like this when i start the application it works but when i close putty it also get close i don't want it to get close 
that's plz help me out

it is like that i open folder cd taimur
then i execute file ./taimur -d
it start working
but when i close putty it stop working
so it is possible that when i close putty it don't stop working

thanks
waiting for your reply

---

### Post by gvartser on 2008-01-26
Use screen, it allows you to start sub shells that you can de attach and reattach when needed. This allows you to log onto the machine start a session inside screen deattach and then log off, but your session is still active.

NOTE!
You may have to install screen, cant remember if comes default during the installation of ubuntu.
```
sudo apt-get install screen
```

1) connect to your Ubuntu using ssh

2) start s new screen session
```
 screen -S <Description>
```

3) Then start your application
 
4) To deattach a screen session:
```
  CTRL + a then d
```

5) To attach a screen session:
```
 screen -r 
```

For further information using screen try:
```
  man screen
```

Best regz,
/g

---

