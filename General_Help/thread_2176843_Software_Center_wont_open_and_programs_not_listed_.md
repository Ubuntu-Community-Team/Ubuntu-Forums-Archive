---
title: "Software Center wont open and programs not listed in dashboard"
date: 2013-09-26
forum: General Help
---

### Post by VegasTamborini on 2013-09-26
The title pretty much says it.

I tried to open Libre office yesterday and nothing came up in the Dash Home Searchbar, so I searched for some other programs and not one came up.
I tried to open the Software Center to check if everything was still installed but it keeps crashing before it loads the homescreen. Reboot didn't help. To be clear, I can still open programs like libre office from the terminal. However, when I tried to open Software Center from the terminal I get the following:

```
user@laptop:~$ software-center
2013-09-26 21:38:50,241 - softwarecenter.ui.gtk3.app - INFO - setting up proxy 'None'
2013-09-26 21:38:50,326 - softwarecenter.db.database - INFO - open() database: path=None use_axi=True use_agent=True
2013-09-26 21:38:51,629 - softwarecenter.backend.reviews - WARNING - Could not get usefulness from server, no username in config file
2013-09-26 21:38:51,920 - softwarecenter.ui.gtk3.app - INFO - show_available_packages: search_text is '', app is None.
2013-09-26 21:38:51,929 - softwarecenter.db.pkginfo_impl.aptcache - INFO - aptcache.open()

```

Then Software Center pops up and freezes and I have to force quit it.

Any suggestions welcome

Thanks

---

### Post by ibjsb4 on 2013-09-26
Try a different [package manager]("http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=synaptic+package+manager&sa=Search&cof=FORID:9"), see if it will work.

[Open a terminal]("https://help.ubuntu.com/community/UsingTheTerminal#Starting_a_Terminal") and enter:

```
sudo apt-get install synaptic
```

---

### Post by VegasTamborini on 2013-09-26
Thanks for the reply, I followed your instructions but unfortunately it didn't help solve the problem

---

### Post by ibjsb4 on 2013-09-26
Will either of them open in terminal?

```
software-center
```

```
gksudo synaptic
```

---

### Post by VegasTamborini on 2013-09-26
Ok, so opening a up a Terminal 'software-center' starts Software Center and then it crashes again. 'gksudo' synaptic opened up the synaptics package manager and it seems to work; I successfully installed and ran virtual box. I don't mind having to use Synaptic Package Manager, however the initial problem still exists that nothing is coming up when I search in the dash. I had to start virtual box from the Terminal.

Thanks for your help so far though. getting virtual box was my main priority.

---

### Post by ibjsb4 on 2013-09-26
I do not run unity or the software center, so better to wait for someone with this experience to help you out.

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=software+center+crash&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=software+center+crash&sa=Search&cof=FORID:9)

Good luck.

---

