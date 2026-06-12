---
title: "CNR not starting up"
date: 2008-05-18
forum: General Help
---

### Post by Alucard-sama on 2008-05-18
I recently installed CNR since I'd heard alot about it and was a little curious.
Anyways when I start it up I get an error about the database not loading or something.
The command line output is this:
> [Debug]"Driver not loaded Driver not loaded" 
[Debug]Query failed:  "" 
[Debug]"Driver not loaded Driver not loaded" 
[Debug]Query failed:  "" 
[Debug]"Driver not loaded Driver not loaded" 
[Debug]Query failed:  "" 
[Debug]"Driver not loaded Driver not loaded" 
[Debug]Query failed:  "" 
[Debug]"Driver not loaded Driver not loaded" 
[Debug]Query failed:  "" 
[Debug]"Driver not loaded Driver not loaded" 
[Debug]Query failed:  "" 
[Debug]"Driver not loaded Driver not loaded" 
[Debug]Query failed:  "" 
[Debug]"Driver not loaded Driver not loaded" 
[Debug]Query failed:  "" 
[Debug]"Driver not loaded Driver not loaded" 
[Debug]Query failed:  "" 
[Debug]"Driver not loaded Driver not loaded" 
[Debug]Query failed:  "" 
[Debug]"Driver not loaded Driver not loaded" 
[Debug]Query failed:  "" 
[Debug]"Driver not loaded Driver not loaded" 
[Debug]Query failed:  "" 
[Debug]"Driver not loaded Driver not loaded" 
[Debug]Query failed:  "" 
[Debug]"Driver not loaded Driver not loaded" 
[Debug]Query failed:  "" 
[Debug]"Driver not loaded Driver not loaded" 
[Debug]Query failed:  "" 
[Debug]"Driver not loaded Driver not loaded" 
[Debug]Query failed:  "" 
[Debug]"Driver not loaded Driver not loaded" 
[Debug]Query failed:  "" 
[Debug]"Driver not loaded Driver not loaded" 
[Debug]Query failed:  "" 
[Debug]"Driver not loaded Driver not loaded" 
[Debug]Query failed:  "" 
[Debug]"Driver not loaded Driver not loaded" 
[Debug]Query failed:  "" 
[Debug]"Driver not loaded Driver not loaded" 
[Debug]Query failed:  "" 
[Debug]"Driver not loaded Driver not loaded" 
[Debug]Query failed:  "" 
[Debug]"Driver not loaded Driver not loaded" 
[Debug]Query failed:  "" 
[Debug]"Driver not loaded Driver not loaded" 
[Debug]Query failed:  "" 
[Debug]"Driver not loaded Driver not loaded" 
[Debug]Query failed:  "" 
[Debug]"Driver not loaded Driver not loaded" 
[Debug]Query failed:  "" 
[Debug]"Driver not loaded Driver not loaded" 
[Debug]Query failed:  "" 
[Debug]"Driver not loaded Driver not loaded" 
[Debug]Query failed:  "" 
[Debug]"Driver not loaded Driver not loaded" 
[Debug]Query failed:  "" 
[Debug]"Driver not loaded Driver not loaded" 
[Debug]Query failed:  "" 
[Debug]"Driver not loaded Driver not loaded" 
[Debug]Query failed:  "" 
[Debug]"Driver not loaded Driver not loaded" 
[Debug]Query failed:  "" 
[Debug]"Driver not loaded Driver not loaded" 
[Debug]Query failed:  "" 
[Debug]"Driver not loaded Driver not loaded" 
[Debug]Query failed:  "" 
[Debug]"Driver not loaded Driver not loaded" 
[Debug]Query failed:  "" 
[Debug]"Driver not loaded Driver not loaded" 
[Debug]Query failed:  "" 
[Debug]"Driver not loaded Driver not loaded" 
[Debug]Query failed:  "" 
[Debug]"Driver not loaded Driver not loaded" 
[Debug]Query failed:  "" 
[Debug]"Driver not loaded Driver not loaded" 
[Debug]Query failed:  "" 
[Debug]"Driver not loaded Driver not loaded" 
[Debug]Query failed:  "" 
[Debug]"Driver not loaded Driver not loaded" 
[Debug]Query failed:  "" 
[Debug]"Driver not loaded Driver not loaded" 
[Debug]Query failed:  "" 
[Debug]"Driver not loaded Driver not loaded" 
[Debug]Query failed:  "" 
[Debug]"Driver not loaded Driver not loaded" 
[Debug]Query failed:  "" 
[Debug]"Driver not loaded Driver not loaded" 
[Debug]Query failed:  "" 
[Debug]"Driver not loaded Driver not loaded" 
[Debug]Query failed:  "" 
[Debug]"Driver not loaded Driver not loaded" 
[Debug]Query failed:  "" 
[Debug]"Driver not loaded Driver not loaded" 
[Debug]Query failed:  "" 
[Debug]"Driver not loaded Driver not loaded" 
[Debug]Query failed:  "" 
[Debug]"Driver not loaded Driver not loaded" 
[Debug]Query failed:  "" 
[Debug]"Driver not loaded Driver not loaded" 
[Debug]Query failed:  "" 
[Debug]"Driver not loaded Driver not loaded" 
[Debug]Query failed:  "" 
[Debug]"Driver not loaded Driver not loaded" 
[Debug]Query failed:  "" 
[Debug]"Driver not loaded Driver not loaded" 
[Debug]Query failed:  "" 
[Debug]"Driver not loaded Driver not loaded" 
[Debug]Query failed:  "" 
[... continues to do this for ages...]
[Debug]"Driver not loaded Driver not loaded" 
type: Initializing stage: 9 msg: Error writing database isDone: 1 id: -1 mode: 0
ProgressDialog::finishAction  actionFinished signal received.
[Debug]hiding chkIcons
[Warning]QSqlQuery::prepare: database not open


Update: Just to be clear I'm using Ubuntu Hardy Heron 8.04 x86.

---

### Post by Mhurst1 on 2008-05-18
How did you install it?

---

### Post by Alucard-sama on 2008-05-18
The deb for Hardy from the official site.

---

### Post by Mhurst1 on 2008-05-18
Are you running 32 or 64 bit?

---

### Post by Alucard-sama on 2008-05-18
32 bit.

---

### Post by Joeb454 on 2008-05-18
I'm not sure if you are aware, but CNR is not supported by Canonical, therefore, technically is not supported by these forums (though other users may of course help if they choose :)).

Just letting you know :)

---

### Post by Alucard-sama on 2008-05-18
Yeah I know but people still help out with "unsupported" packages and apps all the time so I figured I'd try.

---

### Post by Mhurst1 on 2008-05-18
Ok did you log out first before trying to open it?

---

### Post by Alucard-sama on 2008-05-18
Yeah I logged out.

---

### Post by Mhurst1 on 2008-05-18
What version of ubuntu are you using and what flavor?

---

### Post by Alucard-sama on 2008-05-18
Ubuntu Hardy Heron 8.04 32bit

---

### Post by Mhurst1 on 2008-05-18
Ok well it works in kubuntu 8.04 so I don't know why it wouldnt in Ubuntu. You did use gdebi to install it correct?

---

### Post by Vorian on 2008-05-18
OP, you should really seek support from CNR
[http://support.cnr.com/support.jsp](http://support.cnr.com/support.jsp)

---

### Post by Alucard-sama on 2008-05-18
Yes of course, it said all dependencies were satisfied and I clicked Install Package or whatever it says and it installed it and yeah running it doesn't work.

---

### Post by Alucard-sama on 2008-05-19
Okay I figured it. All the info on it said to install qt4-dev-tools but it actually only needs libqt4-sql-sqlite which just happens to be one of qt4-dev-tools dependencies.

---

