---
title: "Apache or XAMPP publish"
date: 2008-05-06
forum: General Help
---

### Post by nesh87 on 2008-05-06
Hello,

im working on a local site using XAMPP. Before publishing it i want my friends to check it out. I dont want to upload it, so i thought id allow them access to my local server. Ive installed apache and all, and it works. When i try localhost, i get the "It works". When i access it using the IP from the "connection information" it also works. But when i use the ip from whatismyip.com (which i think is called the external address) it doesnt work. Ive searched for any tutorials to help me do what i want, couldnt find. I tried giving a friend the ip address from the connection information 10.0.xxx.xxx and he cant connect.

Sorry for the long and confusing post, can i achieve this anyhow?

---

### Post by Go_Bucks on 2008-05-06
If you have a router, you will not be able to view the site using that ip unless you set your router to forward port 80 to the computer running Apache.

---

### Post by nesh87 on 2008-05-06
i dont have a router, I connect to a wireless network provided by in my apartment.

---

### Post by Monicker on 2008-05-07
> **nesh87 said:**
> i dont have a router, I connect to a wireless network provided by in my apartment.

That wireless is probably provided via an access point/router owned by the apartment complex.  Port forwarding would need to be configured on that device.

---

### Post by Go_Bucks on 2008-05-07
He took the words right out of my mouth.

---

### Post by wreisin on 2008-05-07
If getting access to the router is not an option, you can always pay for hosting.  Many places offer really cheap plans ( < $4 / month) for basic needs, and they'll give you shell access, so you can script all your file syncing.

---

