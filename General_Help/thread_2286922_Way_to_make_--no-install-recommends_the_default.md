---
title: "Way to make --no-install-recommends the default?"
date: 2015-07-15
forum: General Help
---

### Post by greg2lapa on 2015-07-15
Is there way to modify apt-get so that the default is to install packages with only dependencies and no recommendations? Then if I want recommendations to be installed, I could add an option like "sudo apt-get install --install-recommends"?

---

### Post by v3.xx on 2015-07-15
Synaptic has that option

[ATTACH=CONFIG]263222[/ATTACH]

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=synaptic+package+manager&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=synaptic+package+manager&sa=Search&cof=FORID:9)

---

### Post by matt_symes on 2015-07-15
Hi

Create an alias for it in ~/bashrc and use that alias to install the software.

Kind regards

---

### Post by steeldriver on 2015-07-15
It should be possible to create an entry

```

APT::Install-Recommends "false";

```

in /etc/apt/apt.conf or in a custom file such as /etc/apt/apt.conf.d/99local, however I've never tried it

---

### Post by matt_symes on 2015-07-15
Hi

> **steeldriver said:**
> It should be possible to create an entry

```

APT::Install-Recommends "false";

```

in /etc/apt/apt.conf or in a custom file such as /etc/apt/apt.conf.d/99local, however I've never tried it

Good call !

Kind regards

---

### Post by greg2lapa on 2015-07-15
> **steeldriver said:**
> It should be possible to create an entry

```

APT::Install-Recommends "false";

```

in /etc/apt/apt.conf or in a custom file such as /etc/apt/apt.conf.d/99local, however I've never tried it

Is there then an option to install recommends after the creation of the apt.conf file (e.g., sudo apt-get install --install-recommends)? Or would installing recommends require disabling the apt.conf.d file?

Is the file "apt.conf" or "apt.conf.d". I've seen both specified in different places across the internet.

---

### Post by CantankRus on 2015-07-15
If more often than not you don't want to install recommends, 
change in synaptic as **v3.xx** showed in post #2 then if you want to include recommends use the [COLOR="#FF0000"]option[/COLOR] via terminal...
```
sudo apt-get install [COLOR="#FF0000"]--install-recommends[/COLOR] [COLOR="#696969"]<package>[/COLOR]
```

Changing the preference in synaptic, edits the **/etc/apt/apt.conf.d/99synaptic** file as steeldriver showed in post #4
thus changes the setting when you run apt-get.

---

