---
title: "Unable to update my system. Various errors"
date: 2013-05-11
forum: General Help
---

### Post by Peterfc on 2013-05-11
I keep getting a number of Errors.

System program problem detected. Do you want to report the problem now? Cancel or Report problem.

Then i get 

Task cannot be monitored or controlled. The conection to the Daemon was lost the background Daemon probably crashed. Details. Close.

Then when i click details i get

It seems that the Daemon Died.

If i go to Software updater, Software Centre and Software sources. None stay open they all flash onto the screen and then off. Then i get error messages.

---

### Post by ibjsb4 on 2013-05-11
Open the software center in terminal and see what it says.

```
software-center
```

---

### Post by Peterfc on 2013-05-11
Hi 

Thanks for the reply

I have copied and pasted the message from the terminal. The Software center just flashed up on screen.

Peter

anthonycalder@anthonycalder-System-Product-Name:~$ software-center
2013-05-11 18:55:26,845 - softwarecenter.ui.gtk3.app - INFO - setting up proxy 'None'
2013-05-11 18:55:26,854 - softwarecenter.db.database - INFO - open() database: path=None use_axi=True use_agent=True
2013-05-11 18:55:27,576 - softwarecenter.backend.reviews - WARNING - Could not get usefulness from server, no username in config file
2013-05-11 18:55:27,721 - softwarecenter.ui.gtk3.app - INFO - show_available_packages: search_text is '', app is None.
2013-05-11 18:55:27,790 - softwarecenter.db.pkginfo_impl.aptcache - INFO - aptcache.open()
Segmentation fault (core dumped)

---

### Post by ibjsb4 on 2013-05-11
Im not having any luck finding a fix for this :(

[https://www.google.com/search?client=ubuntu&channel=fs&q=softwarecenter.db.pkginfo_impl.aptcache+-+INFO+-+aptcache.open%28%29+Segmentation+fault+%28core+dumped%29&ie=utf-8&oe=utf-8#q=softwarecenter.db.pkginfo_impl.aptcache+-+INFO+-+aptcache.open%28%29+Segmentation+fault+%28core+dumped%29&client=ubuntu&hs=iFv&channel=fs&ei=8YyOUbmoLc3BiwLO2oDYAw&start=0&sa=N&bav=on.2,or.r_qf.&bvm=bv.46340616,d.cGE&fp=b53320268759243f&biw=1024&bih=582](https://www.google.com/search?client=ubuntu&channel=fs&q=softwarecenter.db.pkginfo_impl.aptcache+-+INFO+-+aptcache.open%28%29+Segmentation+fault+%28core+dumped%29&ie=utf-8&oe=utf-8#q=softwarecenter.db.pkginfo_impl.aptcache+-+INFO+-+aptcache.open%28%29+Segmentation+fault+%28core+dumped%29&client=ubuntu&hs=iFv&channel=fs&ei=8YyOUbmoLc3BiwLO2oDYAw&start=0&sa=N&bav=on.2,or.r_qf.&bvm=bv.46340616,d.cGE&fp=b53320268759243f&biw=1024&bih=582)

You could do terminal updates/upgrades until a solution can be found or maybe install synaptic package manager and use that for now.

```
sudo apt-get install synaptic
```

---

### Post by Hekabe on 2013-05-11
I don't really use Software Center, but you could try a total reinstall:
```
sudo apt-get update
sudo apt-get --purge remove software-center
sudo apt-get install software-center
```
The update line isn't really necessary, but it doesn't hurt.

From the a line in the error message it gave you, it looks like there might be a problem with your config file, and this should remove that.

---

### Post by Peterfc on 2013-05-11
Hi Hekabe

Thanks i am now running good.

Thanks to the other posters for there help.

Peter

---

