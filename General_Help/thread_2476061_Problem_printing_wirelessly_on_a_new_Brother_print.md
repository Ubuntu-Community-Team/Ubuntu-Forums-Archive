---
title: "Problem printing wirelessly on a new Brother printer MFC-J1010DW"
date: 2022-06-15
forum: General Help
---

### Post by John_Patrick_Mason on 2022-06-15
I'm having difficulty printing wirelessly on an all-in-one Brother  MFC-J1010DW printer. Before downloading any drivers, I created a static  IP address in my router's administrative console, just for the wireless  printer. I was, then, able to successfully connect the printer to my  Wi-Fi network using the static IP address that I created.

I, then, went  on the [support page]("https://support.brother.com/g/b/downloadtop.aspx?source_c=cinst&c=us&lang=en&prod=mfcj1010dw_us_eu_as")  for the MFC-J1010DW printer and made sure to click on "Linux" and,  then, "deb". After that, I was redirected to a new page where I'm given  the opportunity to download a bunch of drivers. Not being sure which  driver to download, I downloaded the "Driver Install Tool" under  "Utilities". I, then, followed the instructions by typing into a  terminal:

```

cd Downloads
gunzip linux-brprinter-installer-2.2.3-1.gz
sudo bash linux-brprinter-installer-2.2.3-1

```

It, then, asked me to specify the model of the printer, so I typed:

```

MFC-J1010DW

```

It, then, asked me to specify the URI of the printer, so I first typed:

```

I

```

to specify that I wanted to enter an IP address.

Lastly, I proceeded to enter the printer's static IP address without the "https://" part.

The terminal then downloaded a bunch of packages, yet, for some reason, I still can't print anything wirelessly.

What am I doing wrong?

---

### Post by mIk3_08 on 2022-06-16
> **John_Patrick_Mason said:**
> I'm having difficulty printing wirelessly on an all-in-one Brother  MFC-J1010DW printer. Before downloading any drivers, I created a static  IP address in my router's administrative console, just for the wireless  printer. I was, then, able to successfully connect the printer to my  Wi-Fi network using the static IP address that I created.

I, then, went  on the [support page]("https://support.brother.com/g/b/downloadtop.aspx?source_c=cinst&c=us&lang=en&prod=mfcj1010dw_us_eu_as")  for the MFC-J1010DW printer and made sure to click on "Linux" and,  then, "deb". After that, I was redirected to a new page where I'm given  the opportunity to download a bunch of drivers. Not being sure which  driver to download, I downloaded the "Driver Install Tool" under  "Utilities". I, then, followed the instructions by typing into a  terminal:

```

cd Downloads
gunzip linux-brprinter-installer-2.2.3-1.gz
sudo bash linux-brprinter-installer-2.2.3-1

```

It, then, asked me to specify the model of the printer, so I typed:

```

MFC-J1010DW

```

It, then, asked me to specify the URI of the printer, so I first typed:

```

I

```

to specify that I wanted to enter an IP address.

Lastly, I proceeded to enter the printer's static IP address without the "https://" part.

The terminal then downloaded a bunch of packages, yet, for some reason, I still can't print anything wirelessly.

What am I doing wrong?

Have you tried to detect your printer wirelessly using your Linux Ubuntu machine and installed it.
> **John_Patrick_Mason said:**
> 
It, then, asked me to specify the URI of the printer, so I first typed:

By the way,  Device URI is something like this.
```
ipp://
```

---

### Post by web-user on 2022-06-18
I think you should check your CUPS (localhost:631) settings. Also don't forget setup printer driver in the web panel. If it's not there, download it from official website and upload it.

---

