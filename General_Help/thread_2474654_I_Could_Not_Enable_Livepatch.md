---
title: "I Could Not Enable Livepatch"
date: 2022-05-05
forum: General Help
---

### Post by matthew-cats-dogs on 2022-05-05
I am using Ubuntu Desktop 22.04 and I recently accessed Software and Updates and then navigated to Livepatch but I got the message "Could not enable Livepatch. Please try again." when I tried to enable it. I have an Ubuntu Advantage subscription attached. Is there a way to fix this or is this an error on Ubuntu's end that needs to be fixed?

---

### Post by matthew-cats-dogs on 2022-05-06
I have Ubuntu Firewall (UFW) set up and enabled, and I am getting the latest system and security updates, so I am doing well with Ubuntu. Maybe Livepatch is enabled but I am just not seeing it.

---

### Post by mIk3_08 on 2022-05-06
> **matthew-cats-dogs said:**
> I have Ubuntu Firewall (UFW) set up and enabled, and I am getting the latest system and security updates, so I am doing well with Ubuntu. Maybe Livepatch is enabled but I am just not seeing it.
can you run this command in you terminal, To access terminal in your Linux Ubuntu Desktop System you can just pressing ctrl and alt + t or Just find it to the installed application in your Linux Ubuntu Operating System. Regards and Cheers
```
sudo ua status
```

---

### Post by matthew-cats-dogs on 2022-05-08
> **mIk3_08 said:**
> can you run this command in you terminal, To access terminal in your Linux Ubuntu Desktop System you can just pressing ctrl and alt + t or Just find it to the installed application in your Linux Ubuntu Operating System. Regards and Cheers
```
sudo ua status
```

I entered 'sudo ua status' inside of the terminal and I discovered I had to enable 'esm-infra' and 'livepatch' and I did so. Thanks!

---

### Post by mIk3_08 on 2022-05-08
> **matthew-cats-dogs said:**
> I entered 'sudo ua status' inside of the terminal and I discovered I had to enable 'esm-infra' and 'livepatch' and I did so. Thanks!
can you run this command below in your terminal. Regards and cheers.
```
hostnamectl status
```

---

### Post by mIk3_08 on 2022-05-09
> **mIk3_08 said:**
> can you run this command below in your terminal. Regards and cheers.
```
hostnamectl status
```
And paste the result here in thread. Thanks

---

