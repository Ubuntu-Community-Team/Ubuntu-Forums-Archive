---
title: "HOWTO: How I got firestarter working with my VPN"
date: 2006-09-27
forum: General Help
---

### Post by Kashirigi on 2006-09-27
I don't know about anyone else, but I found guarddog to be kind of irritating. There's nothing I could put my finger on, but there you go.

So I switched to firestarter. Then I couldn't connect with my VPN. That didn't make me feel better. But I persevered.

Here's what I did.

I looked on the firestarter website ([http://www.fs-security.com/docs/vpn.php](http://www.fs-security.com/docs/vpn.php)) and added the following to my /etc/firestarter/user-pre file (because I'm using a Microsoft VPN)

[FONT="Fixedsys"]
# Forward PPTP VPN client traffic
$IPT -A FORWARD -i $IF -o $INIF -p tcp --dport 1723 -m state --state NEW,ESTABLISHED,RELATED -j ACCEPT
$IPT -A FORWARD -i $IF -o $INIF -p 47 -m state --state NEW,ESTABLISHED,RELATED -j ACCEPT
$IPT -A FORWARD -i $INIF -o $IF -p 47 -m state --state NEW,ESTABLISHED,RELATED -j ACCEPT
[/FONT]

Then I added this to the top of the same file, thanks to the very last post in this thread ([http://www.webservertalk.com/message1620504.html](http://www.webservertalk.com/message1620504.html))

[FONT="Fixedsys"]
# Enable eth1 with vpn -- edit the second line appropriately for your vpn
$IPT -A INPUT -i eth1 -p all -s 0.0.0.0/0 -j ACCEPT
$IPT -A OUTPUT -p all -d 142.103.200.0/0 -j ACCEPT
$IPT -A FORWARD -i eth1 -p all -s 0.0.0.0/0 -d 0.0.0.0/0 -j ACCEPT
[/FONT]

As it says, edit the second line for your vpn (and the first and third for your appropriate interface)

It's not done yet.

Find out if you have the kernel module ip_conntrack_pptp installed.


[FONT="Fixedsys"]
lsmod | grep conntrack
[/FONT]

If you see ip_conntrack_pptp in the output you're fine.

Otherwise

[FONT="Fixedsys"]
sudo modprobe ip_conntrack_pptp
[/FONT]

To make sure that this module loads every time, add 

[FONT="Fixedsys"]ip_conntrack_pptp[/FONT]  to the end of /etc/modules 

[FONT="Fixedsys"]
sudo gedit /etc/modules
[/FONT]

If you'd like, flush iptables
[FONT="Fixedsys"]sudo iptables -F[/FONT] (It's the only way to be sure).
This step probably isn't necessary.

Now, restart firestarter
[FONT="Fixedsys"]
sudo /etc/init.d/firestarter restart
[/FONT]

Don't forget to configure firestarter as shown in this post:
[http://www.ubuntuforums.org/archive/index.php/t-77035.html](http://www.ubuntuforums.org/archive/index.php/t-77035.html)

Hey presto! Firestarter should now work with your VPN setup.

I hope this works with someone else, too. Also, keep in mind that I barely know what I'm doing with linux, seeing as I switched over from the dark side about six months ago. Please feel free to correct any outrageous errors.

---

### Post by Crick on 2007-08-05
Hi, hopefully this guide/HOWTO/DIY doesn't need a new thread.

Personally, I found guarddog to be (much) easier. The following will enable access to ping and rdesktop across a MS PPTP VPN.

Here's how to do it:
1. Search for "guarddog" in synaptic, install.

2. Open up terminal,
> gksudo guarddog &

2.5 Click on "Advanced" tab, click "New Protocol", and name it "rdesktop", of type TCP and Port 3389.

3. Click on "Protocol" tab.

4. Make sure that "Internet" in Defined Network Zones is highlighted.

5. In Zone Properties, -> Click on "File Transfer", ensure that HTTP and HTTPS are checked (otherwise you won't be able to use the web. Check here to see if there's anything else you need enabled).

6. Click on "Network". Ensure DNS (for using the web), ping and PPTP are checked. If you need SSH, it's in Interactive Session.

7. Check rdesktop in User Defined.

8. Click "Apply".

Should be good to go, and beats hacking text files.

I agree that firestarter is prettier, and has the "event" window to see what is going on if you ever want to see if someone is probing your machine or something. I think the key to grok guarddog is to realize that most of the stuff you want to do is in "internet", if you read under the Zone Properties: "Protocols served from zone "Internet" to clients in zones:" 

This means that a check in a box under the column "local" will enable your computer to access something outside, but not vice versa. For most applications, you want to be able to access stuff outside, but block everything from accessing your machine. (I think this is how it works. Correct me if I'm wrong.)

---

### Post by poctob on 2007-08-08
Another way to enable VPN routing via firestarter:
go to Preferences->Network Settings
choose Ethernet Device (eth0)  (yours may be different) as Internet connected network device
choose Routed IP Tunnel (tun0) (yours may be different) as Local network connected device
place a check mark in Enable Internet Connection Sharing box
stop and restart Firestarter.

---

### Post by Jopjop on 2007-09-11
poctob: excellent!
Finally a simple way to make my university vpn connection work with Firestarter.
Thank you.

---

