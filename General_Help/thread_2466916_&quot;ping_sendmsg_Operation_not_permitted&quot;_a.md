---
title: "&quot;ping: sendmsg: Operation not permitted&quot; after setting UFW to deny out || 20.04"
date: 2021-09-10
forum: General Help
---

### Post by linuxyogi on 2021-09-10
Hi,
I have always used ufw with deny all in & allow all out. Yesterday for the first time I had set ufw to deny all out. I have added outgoing ports one by one as per my needs. Now I can browse the web, Thunderbird is working. Problem is I cant ping any IP. When I try to ping I see this :

```
$ ping 8.8.8.8
PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.
ping: sendmsg: Operation not permitted
ping: sendmsg: Operation not permitted
ping: sendmsg: Operation not permitted
^C
--- 8.8.8.8 ping statistics ---
3 packets transmitted, 0 received, 100% packet loss, time 2032ms

```

How do I enable ping ?

---

### Post by The Cog on 2021-09-10
Allow ping requests out:
```
iptables -A OUTPUT -p icmp --icmp-type 8 -j ACCEPT
```
Ping is a type of ICMP packet. Type 8 is a ping request.
Type 0 is an echo reply, but as long as your incoming rules allow RELATED,ESTABLISHED this will be enough and you don't need an extra rule to allow the replies in.

---

### Post by linuxyogi on 2021-09-10
> **The Cog said:**
> Allow ping requests out:
```
iptables -A OUTPUT -p icmp --icmp-type 8 -j ACCEPT
```
Ping is a type of ICMP packet. Type 8 is a ping request.
Type 0 is an echo reply, but as long as your incoming rules allow RELATED,ESTABLISHED this will be enough and you don't need an extra rule to allow the replies in.

It worked. That really helped. Thanks a lot.

Is there a way to take a backup of ufw configuration so that if I reinstall Lubuntu I can restore my current config ?

---

### Post by linuxyogi on 2021-09-11
@The Cog

I am facing an issue. After using 

```
iptables -A OUTPUT -p icmp --icmp-type 8 -j ACCEPT
```

I am able to ping but as soon as I reboot I am again getting 

```
$ ping 8.8.8.8
PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.
ping: sendmsg: Operation not permitted
ping: sendmsg: Operation not permitted
ping: sendmsg: Operation not permitted
^C
--- 8.8.8.8 ping statistics ---
3 packets transmitted, 0 received, 100% packet loss, time 2056ms



```

How do enable ping permanently ?

---

### Post by The Cog on 2021-09-11
I don't know. How did you configure the firewall in the first place? There are many firewall configuration utilities, each with their own rules and files. Look to configure the rule in the one you use (ufw or gufw perhaps?)
The iptables command I posted above only affects the running iptables, so it is lost when you reboot, as you have discovered.
If you're not sure how to configure your firewall, tell us which one you use and someone should be able to tell you how to add that rule permanently. Probably not me though, as I have never used anything other than home-written iptables scripts, and these days I use nftables instead anyway.

---

### Post by linuxyogi on 2021-09-11
> **The Cog said:**
> I don't know. How did you configure the firewall in the first place? There are many firewall configuration utilities, each with their own rules and files. Look to configure the rule in the one you use (ufw or gufw perhaps?) 

_**I am using ufw.**_ I have never installed the GUI gufw coz during all these years all I did was 

```
sudo ufw default deny
sudo systemctl start ufw
sudo  systemctl enable ufw
```

I don't need any open ports. So its been an easy process so far. But now that I am blocking outbound ports too things are different. I got an idea about which outbound ports to open for allowing day to day stuff like web browsing, email, etc by reading [this askubuntu thread]("https://askubuntu.com/questions/448836/how-do-i-with-ufw-deny-all-outgoing-ports-excepting-the-ones-i-need").

**Again, all I am looking for is way to permanantly enable outgoing ping.**

You mention that you are using NFTABLES. I was using an Arch based distro for some months & under Arch I too was using NFTABLES.

If NFTABLES is the new thing then why is Ubuntu still using IPTABLES ? Why hasn't the Ubuntu team replace IPTABLES with NFTABLES ?

---

### Post by The Cog on 2021-09-12
I originally said I couldn't find how to specify the direction (in/out) when entering a rule. My apologies - I just didn't read properly. It's there under "RULE SYNTAX".
The protocol you want to enable is called echo-request I think this just might be the right incantation:
**ufw allow in proto echo-request**

---

### Post by The Cog on 2021-09-15
Bump because I've significantly edited my last comment. In case  linuxyogi is still in need of an answer, I think that may be it.

---

### Post by linuxyogi on 2021-09-23
@TheCog
Sorry for the late reply. I didn't receive any email notification for your replies. First the thread visit count of thread stopped working & now the email notifications have stopped. People who maintain this forum should do something. The email notifications are unpredictable meaning sometimes I get them sometimes I don't.

Before I apply 

```
**ufw allow in proto echo-request**
```

I have a question. Since I started using Ubuntu I have always set ufw to deny all in and allow all out. I never had to open any incoming ports. So why **ufw allow [COLOR=#ff0000]in[/COLOR] proto echo-request** ?
Why not [B]ufw allow [COLOR=#ff0000]out[/COLOR] proto echo-request ?


[/B]Since I can no longer rely on email notifications I will refresh this page every 1/2 hour. Please leave your reply.

---

### Post by The Cog on 2021-09-23
Because I was in a hurry when I scribbled that note. Doh! You are quite right - you need to allow it **out**, of course. Sorry.

---

### Post by linuxyogi on 2021-09-23
> **The Cog said:**
> Because I was in a hurry when I scribbled that note. Doh! You are quite right - you need to allow it **out**, of course. Sorry.

The command is not working 

```
$ sudo ufw allow out proto echo-request
[sudo] password for <snip>:           
ERROR: Need 'to' or 'from' clause


```

---

