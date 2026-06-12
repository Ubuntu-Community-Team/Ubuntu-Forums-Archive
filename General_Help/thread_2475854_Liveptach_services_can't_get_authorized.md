---
title: "Liveptach services can't get authorized"
date: 2022-06-09
forum: General Help
---

### Post by zorono on 2022-06-09
Hello every Creature,
I can't login into my Ubuntu accounts through gnome-control-center's "Online Accounts" Tab since it is raising error with "Error Connecting Ubuntu Single Sign-On server: \n Something went wrong, please try again"




and when i try to enable livepatch (`ua enable livepatch`) it fails:
```
One moment, checking your subscription first
Stderr: Could not retrieve client information.: GET request to "https://livepatch.canonical.com/v1/client/{...}/info" failed




Stdout:
Unable to enable Livepatch: Failed running command '/snap/bin/canonical-livepatch enable <REDACTED>' [exit(1)]. Message: Could not retrieve client information.: GET request to "https://livepatch.canonical.com/v1/client/{...}/info" failed




Unable to determine current instance-id
```




and when I try to enable livepatch(`canonical-livepatch enable <TOKEN>`)
```
failed to register client: POST request to "https://livepatch.canonical.com/v1/client/{...}" failed
```




and please note that I am running a Ubuntu 22.04 LTS (AMD64) based machine.
and please additionally note that i tried
1. [https://askubuntu.com/questions/1270869/canonical-livepatch-service-stopped-working](https://askubuntu.com/questions/1270869/canonical-livepatch-service-stopped-working)
2. [https://askubuntu.com/questions/1264961/canonical-livepatch-failed-when-i-tried-to-enable-token](https://askubuntu.com/questions/1264961/canonical-livepatch-failed-when-i-tried-to-enable-token)
3. [https://askubuntu.com/questions/1142602/canonical-livepatch-internal-error](https://askubuntu.com/questions/1142602/canonical-livepatch-internal-error)
4. [https://askubuntu.com/questions/1376275/canonical-livepatch-has-experienced-an-internal-error-on-start-up](https://askubuntu.com/questions/1376275/canonical-livepatch-has-experienced-an-internal-error-on-start-up)
5. [https://askubuntu.com/questions/1271580/cant-enable-canonical-livepatch-on-ubuntu-20-04-1-lts](https://askubuntu.com/questions/1271580/cant-enable-canonical-livepatch-on-ubuntu-20-04-1-lts)
6. [https://askubuntu.com/questions/1047839/signing-into-ubuntu-one-for-livepatch](https://askubuntu.com/questions/1047839/signing-into-ubuntu-one-for-livepatch)
7. [https://ubuntuforums.org/showthread.php?t=2420465](https://ubuntuforums.org/showthread.php?t=2420465)
8. [https://askubuntu.com/questions/1403568/can-not-enable-livepatch-service-on-22-04](https://askubuntu.com/questions/1403568/can-not-enable-livepatch-service-on-22-04)
9. [https://askubuntu.com/questions/1069356/ubuntu-single-sign-on-account-stuck-on-connecting](https://askubuntu.com/questions/1069356/ubuntu-single-sign-on-account-stuck-on-connecting)
10. [https://askubuntu.com/questions/1361658/ubuntu-20-04-cannot-login-ubuntu-single-sign-on-account-something-went-wrong-p](https://askubuntu.com/questions/1361658/ubuntu-20-04-cannot-login-ubuntu-single-sign-on-account-something-went-wrong-p)




but none of them worked!!






Please note that i previously asked the same question on [Askubuntu]("https://askubuntu.com/questions/1409790/liveptach-services-cant-get-authorized") 19 day ago...
----------
## System Specifications




* Operating System: Ubuntu 22.04
* Life cycle: LTS
* Architecture: AMD64
* canonical-livepatch: v10.2.3
* ubuntu-advantage-desktop-daemon: v1.9~22.04.1
* ubuntu-advantage-pro: v27.8~22.04.1
* ubuntu-advantage-tools: v27.8~22.04.1
* Kernel version (`uname -a`): 5.15.0-37

---

### Post by mIk3_08 on 2022-06-09
> **zorono said:**
> Hello every Creature,
I can't login into my Ubuntu accounts through gnome-control-center's "Online Accounts" Tab since it is raising error with "Error Connecting Ubuntu Single Sign-On server: \n Something went wrong, please try again"
and when i try to enable livepatch (`ua enable livepatch`) it fails:
One moment, checking your subscription first
Stderr: Could not retrieve client information.: GET request to "https://livepatch.canonical.com/v1/client/{...}/info" failed

Before you can successfully run the livepatch you should have successfully register/subscribe to Ubuntu Advantage for Infrastructure. 
When you successfully subscribe, canonical will give you your unique subscription token. 
This will help you enable your Livepatch 
&#9989;To enable Livepatch; you must install Livepatch first
```
install canonical-livepatch
```
&#9989;Then use your Livepatch  token to enable your Livepatch
```
ua enable livepatch
```
Good Luck. Regards and cheers.

---

### Post by zorono on 2022-06-10
> **mIk3_08 said:**
> Before you can successfully run the livepatch you should have successfully register/subscribe to Ubuntu Advantage for Infrastructure. 
When you successfully subscribe, canonical will give you your unique subscription token. 
This will help you enable your Livepatch 
&#9989;To enable Livepatch; you must install Livepatch first
```
install canonical-livepatch
```
&#9989;Then use your Livepatch  token to enable your Livepatch
```
ua enable livepatch
```
Good Luck. Regards and cheers.
Excuse me but i am sure you misunderstood me...

**canonical-livepatch enable <TOKEN>**: ```
failed to register client: POST request to "https://livepatch.canonical.com/v1/client/<MACHINEID>" failed
```
**ua enable livepatch**: ```
One moment, checking your subscription firstStderr: Could not retrieve client information.: GET request to "https://livepatch.canonical.com/v1/client/<MACHINEID>/info" failed


Stdout: 
Unable to enable Livepatch: Failed running command '/snap/bin/canonical-livepatch enable <REDACTED>' [exit(1)]. Message: Could not retrieve client information.: GET request to "https://livepatch.canonical.com/v1/client/<MACHINEID>/info" failed

```

---

### Post by mIk3_08 on 2022-06-11
> **zorono said:**
> Excuse me but i am sure you misunderstood me...

**canonical-livepatch enable <TOKEN>**: ```
failed to register client: POST request to "https://livepatch.canonical.com/v1/client/<MACHINEID>" failed
```
**ua enable livepatch**: ```
One moment, checking your subscription firstStderr: Could not retrieve client information.: GET request to "https://livepatch.canonical.com/v1/client/<MACHINEID>/info" failed


Stdout: 
Unable to enable Livepatch: Failed running command '/snap/bin/canonical-livepatch enable <REDACTED>' [exit(1)]. Message: Could not retrieve client information.: GET request to "https://livepatch.canonical.com/v1/client/<MACHINEID>/info" failed

```
I just want to clarify this... 
One of your concern is that you want to enable your Livepatch. right? 
2nd. Do you already have your livepatch token?

---

### Post by zorono on 2022-06-11
**[COLOR=#000000]* you want to enable your Livepatch. right? [/COLOR]**[COLOR=#000000]yes i do..
*** **[/COLOR]**[COLOR=#000000]Do you already have your livepatch token? [/COLOR]**[COLOR=#000000]&#8203;yes i do..[/COLOR]

---

### Post by mIk3_08 on 2022-06-12
> **zorono said:**
> **[COLOR=#000000]* you want to enable your Livepatch. right? [/COLOR]**[COLOR=#000000]yes i do..
*** **[/COLOR]**[COLOR=#000000]Do you already have your livepatch token? [/COLOR]**[COLOR=#000000]&#8203;yes i do..[/COLOR]
Try to follow this instructions in sequence.
This is to remove your Livepatch: If you have successfully installed and successfully attach your Livepatch token but was not successfully enabled the Livepatch.
Run this command below: 
```
sudo snap run canonical-livepatch disable
sudo snap remove canonical-livepatch
sudo rm /etc/machine-id
sudo systemd-machine-id-setup
sudo snap install canonical-livepatch

```But if you haven't successfully run Livepatch but have attempted to install it and surely wasn't successfully attach your Livepatch token 
run this command below.
```
sudo snap run canonical-livepatch disable
sudo snap remove canonical-livepatch

```
But If you have attempted to attach your unique token here
run this command below:
```

sudo rm /etc/machine-id
sudo systemd-machine-id-setup

```
Run the command below for fresh install of Livepatch and Livepatch unique token attachment
```

sudo snap install canonical-livepatch
sudo canonical-livepatch enable  [unique token]

```Good luck. Regards and cheers.

---

### Post by zorono on 2022-06-12
Thank you alot dude, after trying your recommended commands it seems to be working again and got authorized!!! 

```

sudo snap run canonical-livepatch disable
sudo snap remove canonical-livepatch
sudo rm /etc/machine-id /var/lib/dbus/machine-id
sudo systemd-machine-id-setup
sudo dbus-uuidgen --ensure=/etc/machine-id
sudo canonical-livepatch enable [unique token]
sudo snap forget [snapshot ID]
sudo snap install canonical-livepatch
sudo snap save

```

---

### Post by mIk3_08 on 2022-06-13
> **zorono said:**
> Thank you alot dude, after trying your recommended commands it seems to be working again and got authorized!!! 

Your welcome Sir. If you have time Please mark this thread as Solve. Regards and Cheers.

---

