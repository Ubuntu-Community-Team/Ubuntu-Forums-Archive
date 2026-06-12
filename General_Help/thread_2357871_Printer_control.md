---
title: "Printer control"
date: 2017-04-06
forum: General Help
---

### Post by Camilia on 2017-04-06
I can not stop my printer from printing. 

1. I tried opening the printer in system settings and cancel job. 
2. Turing enabled off stopped it but then can not print anything. So it is just a temporary fix.
3. Unplugged the printer. 
4. In synapse added HPLIP toolbox and any cups. 
5. IN synapse Checked system-config-printer in synapse package manager.
6. In terminal did commands lpq -a and lprm

---

### Post by deadflowr on 2017-04-07
Look at your settings in the cups browser page at
```
localhost:631
```

---

### Post by Camilia on 2017-04-07
> **deadflowr said:**
> Look at your settings in the cups browser page at
```
localhost:631
```
I don't know where the cups browser page is. I don't know what to do with that code. Thus your answer makes no sense to me.

Did sudo apt install cups in terminal = cups is already the newest version

In browser going to localhos:631 = [www.localhost](www.localhost) refused to connect

---

### Post by howefield on 2017-04-07
Put

```
localhost:631
```

into the address bar of your web browser, eg Chromium or Firefox, and press enter, it will take you to a page where you can administer your printer(s).

---

### Post by Camilia on 2017-04-07
> **howefield said:**
> Put

```
localhost:631
```

into the address bar of your web browser, eg Chromium or Firefox, and press enter, it will take you to a page where you can administer your printer(s).

I did that before you replied. Result was localhos&#8217;s server DNS address could not be found.

Printer finished printing several jobs. Hopefully the next time using code lprm in terminal will clear jobs if needed.

Which I could get better control of the printer

---

### Post by howefield on 2017-04-07
Perhaps a typo.. ?

localhos:631 should be  localhost:631

---

### Post by Camilia on 2017-04-07
> **howefield said:**
> Perhaps a typo.. ?

localhos:631 should be  localhost:631

Result was localhost refused to connect

For some unknown reason I now have the HPLIP status service in menu bar. It gives me better control of the printer.

---

