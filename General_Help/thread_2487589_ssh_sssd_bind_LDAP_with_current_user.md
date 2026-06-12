---
title: "ssh sssd bind LDAP with current user"
date: 2023-06-09
forum: General Help
---

### Post by iaconeta-65 on 2023-06-09
[COLOR=#202124][FONT=arial]Good morning,[/FONT][/COLOR]
[COLOR=#202124][FONT=arial] is it possible to configure SSH and SSSD by binding to LDAP with the same user who requested ssh access without using a specific service account?Thank you[/FONT][/COLOR][COLOR=#202124][FONT=arial]
[/FONT][/COLOR]
Thanks

---

### Post by ActionParsnip on 2023-06-09
[https://techwolf12.nl/blog/ssh-authentication-ldap](https://techwolf12.nl/blog/ssh-authentication-ldap)
Does that help....?

---

### Post by iaconeta-65 on 2023-06-15
> **ActionParsnip said:**
> [https://techwolf12.nl/blog/ssh-authentication-ldap](https://techwolf12.nl/blog/ssh-authentication-ldap)
Does that help....?


I can't use certificates, I have to use user and password authentication.
I have a few hundred Ubuntu machines that users need to be able to access remotely via ssh. By policy the service account password expires every 60 days and I don't want to update this password on hundreds of machines. Hence my request (binding to LDAP with the same user who requested ssh access without using a specific service account).

---

### Post by ActionParsnip on 2023-06-15
[https://youtu.be/kSCx3tzC0cA](https://youtu.be/kSCx3tzC0cA)

That looks decent. We use Windows AD at work instead of LDAP but it's basically the same thing

---

### Post by iaconeta-65 on 2023-06-15
> **ActionParsnip said:**
> [https://youtu.be/kSCx3tzC0cA](https://youtu.be/kSCx3tzC0cA)

That looks decent. We use Windows AD at work instead of LDAP but it's basically the same thing

My customer doesn't want that i put the Ubuntu machines in domain.
Can I use this procedure for my case?

---

### Post by ActionParsnip on 2023-06-15
Bizarre but OK. Yeah you can spin up an LDAP box and add add servers to it. There is no detriment to adding Linux systems to AD.

---

### Post by iaconeta-65 on 2023-06-15
> **ActionParsnip said:**
> Bizarre but OK. Yeah you can spin up an LDAP box and add add servers to it. There is no detriment to adding Linux systems to AD.


[COLOR=#202124][FONT=arial]My client doesn't want me to put Ubuntu machines on the domain because there are several hundred of them and not to have to update the domain every time a machine is added or retired.He doesn't want to make any LDAP server side changes or configurations.[/FONT][/COLOR]

---

### Post by ActionParsnip on 2023-06-17
> **iaconeta-65 said:**
> [COLOR=#202124][FONT=arial]My client doesn't want me to put Ubuntu machines on the domain because there are several hundred of them and not to have to update the domain every time a machine is added or retired.He doesn't want to make any LDAP server side changes or configurations.[/FONT][/COLOR]

You update the domain when Windows systems are added and retired....
I don't think your custom understands AD.

---

