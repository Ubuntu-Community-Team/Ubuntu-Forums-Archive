---
title: "Server: Services no longer load!"
date: 2007-10-08
forum: General Help
---

### Post by ieatkittens on 2007-10-08
We had a power outage over the weekend and since I got the server back online none of the services start automatically!

My runlevel is 2 and the symbolic links are intact, and if I manually start the services they start fine...but for some reason they refuse to start up on their own!!

I've tried searching the forums but I haven't been able to find anything relevant...help!

---

### Post by ieatkittens on 2007-10-09
Trying to avoid a reinstall :(

---

### Post by louieb on 2007-10-09
Just did a [Google Linux Search]("http://www.google.com/linux") for** run level**
found this [http://www.userlinux.com/cgi-bin/wiki.pl?Run_Level_Lecture](http://www.userlinux.com/cgi-bin/wiki.pl?Run_Level_Lecture)
Looks like /etc/rc2.d controls what and how services are started.
Haven't had to mess with it myself so don't know much about it. Good luck.

---

### Post by ieatkittens on 2007-10-09
The run-level folders contain the proper symbolic links...the problem is that nothing will run from those folders!

If I manually run the software that it's linked to then it's not an issue, but I don't want to have to start each service individually whenever the server goes down

---

