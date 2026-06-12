---
title: "Ubuntu 16.04 Server - Is it possible to make multiple logins for one Ubuntu account?"
date: 2020-03-31
forum: General Help
---

### Post by mikeaw2010 on 2020-03-31
[COLOR=#242729][FONT=Arial]Lets say that I have a Ubuntu Account that I want to be shared by multiple users, however; I want each user to login to it using their own login credentials for tracking purposes. Is it possible to create lets say 6 different user logins that all access one single account?[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]Lets go a step further, is it also possible to do this with OIDC or SAML?[/FONT][/COLOR]

---

### Post by TheFu on 2020-03-31
i've seen shared secondary accounts, never primary accounts.  They built a custom setup to make that possible Custom kernels for all workstations.  it was for a huge govt contract.  Very little was stock.

Rather than saying step 1 for what you need, could you step back and describe the real end-goal?  Unix systems have allowed teams to work together using their own, authenticated, accounts since the beginning.  i suspect there is an elegant solution to the real problem.

Also, please define "ubuntu account."

---

### Post by dragonfly41 on 2020-03-31
I sometimes use [webmin]("http://www.webmin.com/") for similar purposes (custom commands for different projects). But just be aware that it throws the door open if security is not very tight.

---

### Post by mikeaw2010 on 2020-03-31
Basically we have multiple VM's running Ubuntu 16.04 of which ansible tasks are deployed upon. These tasks are generally deployed under a single specific user account, however; all engineers have access to the same user account. 
For example, we will call this account **primary-account**

What we want to do is give each engineer a login credential so we can identify per logs which engineer made what change or deployed what play.
So each Engineer would have the user account: **Eng1 Eng2 Eng3 **each with separate passwords that when authenticated, will log in to **primary-account** but record all actions done by each specific engineer separately.

---

### Post by TheFu on 2020-03-31
We use "deploy9433" as the Ansible deploy account.  ssh-keys are setup for that account for ansible use.  Each admin still logs into the Ansible deployment server under their own accounts, then uses sudo.

if you want a record of the ansible command used for deployment, just force them to use 
```
sudo -u deploy9433 ansible-playbook name-of-playbook.yaml
```
All sudo commands are logged outside the existing ansible logging that can be configured.

We don't use Tower, but I’d be surprised if the setup for it doesn't address this + logging.

---

### Post by mikeaw2010 on 2020-04-01
Is there a way instead to log ssh connections IP and client mac-address?

---

### Post by TheFu on 2020-04-01
> **mikeaw2010 said:**
> Is there a way instead to log ssh connections IP and client mac-address?

All ssh connections are logged in the normal way for every Unix system.
MAC addresses are at a different network level than ip networking.  Those are part of the physical connection lay on the LAN only.

---

### Post by mikeaw2010 on 2020-04-02
> **TheFu said:**
> All ssh connections are logged in the normal way for every Unix system.
MAC addresses are at a different network level than ip networking.  Those are part of the physical connection lay on the LAN only.

I was figuring as much but wanted to ask anyway.

What do you think is the best way to achieve what I am attempting to accomplish, in the aspect of logging who connects to the primary-account and what commands they issue?

---

### Post by TheFu on 2020-04-02
sudo logs all commands and the userid making those commands.
All ssh connections are logged.

So we are left with the fact that logs are local, by default, and someone with local sudo rights that allow access escalation to root can modify/delete local logs.  That means a remote logging system is necessary. journalctl allows that.  i understand it is much easier to configure than the older, rsyslogd way, but haven't done it myself.

---

