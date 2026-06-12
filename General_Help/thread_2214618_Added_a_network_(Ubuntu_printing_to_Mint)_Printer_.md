---
title: "Added a network (Ubuntu printing to Mint) Printer and Auth Required... Why?"
date: 2014-04-02
forum: General Help
---

### Post by 777funk on 2014-04-02
I've changed this several times by:

```
sudo service cups stop

sudo gedit /etc/cups/printers.conf

>>> Deleting the Auth line of code

sudo service cups start

```

And as soon as I hit print from my Ubuntu machine to the Mint computer (my wife's) the Auth line of code always comes back. Then it says Waiting for Auth (Network) before printing. It's weird because printing on her computer in XP (dual boot machine) works great. Just for some reason my machine is always making me authorize before it will print. It prints just fine locally (on her Mint machine).

And the worst part is my username and password (the Ubuntu unlock screen/sudo password) do not unlock and neither does hers if I type it into the authorization fields from my Ubuntu machine. 
---related to that, if I share a network folder from my machine over our network and require password authorization, my su username and password are supposedly incorrect. It won't let me access the folder. Wouldn't the user and password be my su username?

---

### Post by 777funk on 2014-04-02
any tips?

---

