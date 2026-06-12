---
title: "Redshift"
date: 2022-07-01
forum: General Help
---

### Post by jacksonguitars on 2022-07-01
Dear sirs and ladies!

How do I make redshift work for non admin users?

---

### Post by ajgreeny on 2022-07-01
I do not have any non-admin users on my systems but I wonder if the problem is related to how your redshift detects your location.

Many users use geoclue for this but I do this manually with my latitude and longitude; as my computers are always in the UK that is fine for me.

Here is the content of my ***~/.config/redshift.conf*** from which I have removed all the unnecessary lines that simply explain and comment on the application; those lines do nothing all being commented out with a semi-colon ;
```
[redshift]
temp-day=6500
temp-night=4000
transition=1
adjustment-method=randr
location-provider=manual
[manual]
lat=51.87
lon=-1.48
[randr]
screen=0

```
Give that a try after changing the latitude and longitude to your own location.

---

### Post by aug7744 on 2022-07-01
Redshift not work with wayland

---

### Post by jacksonguitars on 2022-07-02
Thank you, all.

---

