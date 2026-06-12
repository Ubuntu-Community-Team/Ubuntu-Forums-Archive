---
title: "where is Google Chrome in repos"
date: 2015-03-09
forum: General Help
---

### Post by trav9595 on 2015-03-09
how do you get chrome browser?? terminal

---

### Post by slickymaster on 2015-03-09
google-chrome-stable is available on the 3rd Party Repository.

To install it from the terminal, start by adding its key:```
wget -q -O - https://dl-ssl.google.com/linux/linux_signing_key.pub | sudo apt-key add - 
```
Set the repository:```
sudo sh -c 'echo "deb http://dl.google.com/linux/chrome/deb/ stable main" >> /etc/apt/sources.list.d/google.list'
```
And then install the package:```
sudo apt-get update 
sudo apt-get install google-chrome-stable
```

---

### Post by kerry_s on 2015-03-09
i just go to the download site grab the deb & click on it.

---

### Post by trav9595 on 2015-03-09
I did the terminal thing...where is Chrome???? its not showing under the Internet applications  accessories thing...

---

### Post by slickymaster on 2015-03-09
Doesn't it opens if run in the terminal```
google-chrome-stable
```

---

### Post by kerry_s on 2015-03-09
> **trav9595 said:**
> I did the terminal thing...where is Chrome???? its not showing under the Internet applications  accessories thing...

if you did it by terminal then it's probably broken. you need to fix.

```
sudo apt-get -f install
```

that will install the dependency's.

---

