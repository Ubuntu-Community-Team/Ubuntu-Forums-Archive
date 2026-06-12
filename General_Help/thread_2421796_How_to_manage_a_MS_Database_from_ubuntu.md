---
title: "How to manage a MS Database from ubuntu"
date: 2019-06-27
forum: General Help
---

### Post by giobaxx on 2019-06-27
Could you tell me if there is a software like Microsoft SQL Management Studio for Ubuntu? Obviously I don't expect all the features in the Microsoft suite


Tanks

---

### Post by TheFu on 2019-06-27
Might want to check out tools from commercial vendors for this need.  In the old days we used products from Quest like Toad.

---

### Post by dragonfly41 on 2019-06-27
Must it be SQL or will a NoSQL db suffice?

---

### Post by ccor58 on 2019-06-28
I have had some success using LibreOffice-Base and/or OpenOffice-Base and connecting to the MS database tables directly using the correct database connector modules listed in synaptic package manager. If it is an MS Access database it will need one type of connector; an sql type database will require a different type possibly an obdc type. There is also an mdb utilities package in linux that might be of use depending on what you want to accomplish.  You can also create a mySQL or Mariah db on the linux box/server and arrange access so that your windows db manager programs can access those tables with the proper connectors set up. Another option is run a linux/ubuntu host and a windows guest using a virtual box program and do your database in the windows virtual instance using MS SQL or MS Access etc.

---

