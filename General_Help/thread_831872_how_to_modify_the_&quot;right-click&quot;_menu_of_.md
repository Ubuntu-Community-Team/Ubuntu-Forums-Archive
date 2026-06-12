---
title: "how to modify the &quot;right-click&quot; menu of mouse ?"
date: 2008-06-17
forum: General Help
---

### Post by dexter.deepak on 2008-06-17
i have read about this stuf long back..but never tried it.
i now want a menu entry  for restarting tomcat5.5..
it take a long time for me to do the following steps :

cd /etc/init.d
sudo sh tomcat5.5 stop
//then wait until the server stops...maximum 5 secs
sudo sh tomcat5.5 start

can someone help me achieve this ??
i also heard that we can change the "functionality" of right-click
that is, we right-click the mouse and it launches a terminal.

i would be glad to get some support from you guys..this dynamism is the reason i shifted to linux.:guitar:

...and do point out if you think that i should have posted the query in some other forum..

---

### Post by mc4man on 2008-06-17
As far as right click while of limited value you could install nautilus-open-terminal
That will give you a right click open terminal option while on the desktop and when in a dir. or highlighting a folder an open in terminal option (basically a quick way to cd to a dir.)
Of more value would be to create nautilus actions for open gedit as root (files) and open nautilus as root (folders). I would only do so if your the only user due to the potential misuse/damage ect.

---

### Post by prshah on 2008-06-17
> **dexter.deepak said:**
> 
i now want a menu entry  for restarting tomcat5.5..


create a file with this line```

sudo /etc/init.d/tomcat5.5 stop && sleep 6 && sudo /etc/init.d/tomcat5.5 start

```

The advantage of using "&&" is that if for some reason the stop fails, the delay and start will not execute.

Save it in your home directory ("~"), make it executable ```

chmod u+x restarttomcat
```

Now click on System-Preferences-Main Menu-System Tools. Then click on "New Item", and:
for Type choose "Application in terminal",
for Name: anything you like
for command: ~/restarttomcat
for comment: Anything you like.

replace "restarttomcat" with whatever name you have saved the code as.

---

### Post by dexter.deepak on 2008-06-17
> **mc4man said:**
> As far as right click while of limited value you could install nautilus-open-terminal
That will give you a right click open terminal option while on the desktop and when in a dir. or highlighting a folder an open in terminal option (basically a quick way to cd to a dir.)
Of more value would be to create nautilus actions for open gedit as root (files) and open nautilus as root (folders). I would only do so if your the only user due to the potential misuse/damage ect.

i just gave an example as to what i would like to have do by the right click action...meaning i dont want to be specific to just open the terminal...can you give me a "general" approach..like if i want to open "netbeans" if i rightclick anywhere on the screen...
..anyway thanks for the above solution.

---

### Post by mc4man on 2008-06-17
> like if i want to open "netbeans" if i rightclick anywhere on the screen...
I'm sure you noticed that there are different r.click context menus depending on where and or what you are clicking on. The r. click on desktop is the most restrictive one and I don't believe can be added to from nautilus actions which is meant for files and folders.
Nautilus-open-terminal was added but that is an extension controlled by a lib (libnautilus-open-terminal.so)
For what you want creating a launcher or a launcher of a shell script would be better suited

---

### Post by dexter.deepak on 2008-06-18
thanks mac ... i got your point !!

---

