---
title: "Can not set default browser"
date: 2018-01-28
forum: General Help
---

### Post by raleigh3 on 2018-01-28
I have set Seamonkey as default browser within SM and under preferred applications.
  
Yet apps that have a help section always use Firefox to go to their help website.


Any way to stop that?

andyk_~/Downloads$ sudo update-alternatives --config x-www-browser
[sudo] password for andy: 
There is only one alternative in link group x-www-browser (providing /usr/bin/x-www-browser): /usr/bin/firefox
Nothing to configure.

---

### Post by raleigh3 on 2018-01-29
Anyone ?

---

### Post by Dennis N on 2018-01-29
> There is only one alternative in link group x-www-browser (providing /usr/bin/x-www-browser): /usr/bin/firefox
Nothing to configure. 
That means you need to install the other browser as one of the possible alternatives. Then you will be able to choose it. Need help with that?

---

### Post by raleigh3 on 2018-01-29
Yes, please.

---

### Post by Dennis N on 2018-01-29
> **raleigh3 said:**
> Yes, please.
We first need to get the seamonkey executable file location. Firefox is /usr/bin/firefox, so maybe /usr/bin/seamonkey? 

Check for this file (probably it will be a symbolic link) with:
```
ls -l /usr/bin/seamonkey
```

---

### Post by raleigh3 on 2018-01-29
Thanks Dennis.

I kept plugging away and trying different things.
  
I found a fix.

I used this 

```
gksu synaptic-pkexec
```

instead of 

  ```
synaptic-pkexec 

```
 Now when I click on Visit homepage within synaptic, it uses Seamonkey instead of Firefox.

---

### Post by raleigh3 on 2018-01-29
> **Dennis N said:**
> We first need to get the seamonkey executable file location. Firefox is /usr/bin/firefox, so maybe /usr/bin/seamonkey? 

Check for this file (probably it will be a symbolic link) with:
```
ls -l /usr/bin/seamonkey
```

I'll follow your instructions.

Yes, it is in usr/bin.

---

### Post by Dennis N on 2018-01-29
Great. Use the following commands to set up seamonkey as the default browser:

Install it as an alternative browser:
```
sudo update-alternatives --install /usr/bin/x-www-browser x-www-browser /usr/bin/seamonkey 40
```
You can verify it's been installed in the alternatives with:
```
update-alternatives --display x-www-browser
```
Finally, set the default broswer with:
```
sudo update-alternatives --config x-www-browser
```

---

### Post by raleigh3 on 2018-01-29
Thanks.

Works like a charm.

---

