---
title: "sudo vs kdesudo"
date: 2017-05-09
forum: General Help
---

### Post by anon_private on 2017-05-09
I know that using sudo to start a graphics programme can cause permissions problems; but what if kdesudo is used to start a non-graphics programme, would that cause permission problems?

---

### Post by efflandt on 2017-05-09
I don't see why sudo would have any problem with graphics launched from a terminal window, it would simply request your password in the text terminal instead of a gui pop up. A GTK+ gui interface for su or sudo can interchangeably use either gksu or gksudo. If you really want to see if kdesudo works for a non-graphics programme, simultaneously press Ctrl+Alt+F1, log in, then type kdesudo with any command. To return to KDE press Alt+F7.

You could also try kdesudo in a terminal window where it may actually work to run non-graphics in that terminal window, but then what is the point of typing 7 letters and opening another window vs. 4 letters and entering your password in the terminal window.

---

### Post by wildmanne39 on 2017-05-09
Actually you do not run a gui with sudo or the files can become owned by root as the OP stated and it can be a hassle fixing it, gksu and gksudo is depreciated and the best way for now to run gui from the terminal is with sudo -H.

I am not sure that kde can be used to start a non graphic application it might throw an error, I see no reason to do it when that is what sudo is for.

---

### Post by mastablasta on 2017-05-10
> **efflandt said:**
> I don't see why sudo would have any problem with graphics launched from a terminal window, it .

this is still valid explanation: [SIZE=2]http://www.psychocats.net/ubuntu/graphicalsudo
[/SIZE]
except that as mentioned gksudo is deprecated, so use sudo -H instead.

---

