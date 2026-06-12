---
title: "Run app as root on start-up"
date: 2007-05-11
forum: General Help
---

### Post by Znupi on 2007-05-11
I have a webserver installed ([XAMPP](http://apachefriends.org)), and each time I login I have to run the following command to start it:
```

sudo /opt/lampp/lampp start

```
Now, to ease this I have created a launcher on my desktop, with this command:
```

gksudo /opt/lampp/lampp start

```
But I still forget to double-click it sometimes, and I end up leaving my house with the webserver off, which could prove fatal (I have projects & stuff hosted there and need to access them from school)...

How would I be able to automate this? Would adding the second command to the start-up programs in the Sessions menu work? Would it ask me two times for my password, each time I login? Are all the programs listed there run as root, so I can lose the gksudo part?... How?...

---

### Post by Znupi on 2007-05-12
Anyone? :(

---

### Post by kaamos on 2007-05-12
You can add the line (without sudo) to /etc/rc.local. It is run as root on boot.

---

### Post by Znupi on 2007-05-12
That did it. Thanks a lot :)

---

