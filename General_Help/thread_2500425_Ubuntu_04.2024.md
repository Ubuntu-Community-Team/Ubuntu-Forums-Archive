---
title: "Ubuntu 04.2024"
date: 2024-09-01
forum: General Help
---

### Post by jzaragoza on 2024-09-01
When I try to update software, I get this error: Snap Store can't be updated. (null): cannot refresh "snap-store"; snap "snap-store" has running apps (ubuntu-software), pids: 2253.
My computer has been just turned on.
I have Ubuntu 04.2024 just installed by an update of 04.2022.

---

### Post by grahammechanical on 2024-09-01
Are you updating using the Ubuntu Software application? On Ubuntu 24.04 it is called App Centre and it is a snap packaged application. It will give that message because it cannot update itself while it is open. This is what I think.

You can open Software and Updates. That will update applications that are snap packaged and also those that are Debian (deb) packaged. Some snap packaged applications will update automatically if we are connected to the internet when we switch the computer on.

Regards

---

### Post by jzaragoza on 2024-09-02
When I open Sofware and updates, nothing happens. The error in Ubuntu Software, update everything, persists.
Should I try by terminal? With what command?

---

### Post by nicolasdentremont on 2024-09-02
The Snap Store can't update itself while it's running and won't sut itself down for an update.

You'll have to find the Snap Store in the system monitor and kill the process.

Then you can use a terminal to update it with:

```
 snap refresh 
```

---

### Post by jzaragoza on 2024-09-02
Thank you.
But should I do the same thing every time I get the error? Isn´t this a bug of 04.24?

---

### Post by nicolasdentremont on 2024-09-02
> **jzaragoza said:**
> Thank you.
But should I do the same thing every time I get the error? Isn´t this a bug of 04.24?

Most likely. If you are updating snaps with the Snap Store, then it will be running and unable to update itself. It's a strange situation.

---

