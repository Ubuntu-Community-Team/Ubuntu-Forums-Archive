---
title: "Synaptic and Gnome network proxy settings"
date: 2006-10-29
forum: General Help
---

### Post by sav2005 on 2006-10-29
I'm a little puzzled about this one ](*,) - Dapper and Edgy.

I'm behind a firewall at work. I enable System -> Preferences -> Network proxy to enable Gnome-based applications to access the Internet and they work. Except for Synaptic. I have to disable Gnome's proxy settings and enable the network proxy settings in Synaptic. It works, but its a hassle! 

Example:
  =======================================
  |Application | Network Proxy | Result |
  =======================================
  |Epiphany    |    On         | Works  |
  |Synaptic    |    On         | Fails  |
  |Epiphany    |    Off        | Fails  |
  |Synaptic    |    Off        | Works  |
  =======================================

---

### Post by Dr. Nick on 2006-10-29
If i set the gnome proxy up and leave synaptic to "direct connect" it will go through the proxy on edgy, yours fails in that setup?

---

### Post by featherking on 2006-10-29
To configure synaptic for a proxy server, Open synaptic go to Settings>Network and input your proxy configuration.

*Note -> this will also make update-manager run from these proxy settings, i have used this way many times at school and it works great.

---

### Post by nardis_Miles1 on 2006-10-30
You can  also edit the apt.conf file in /etc/apt 

inserting the lines:

Acquire
{
http
{
 Proxy "http://yourproxy.yourdomain:yourport";
 };
};

will get you there. There is another wrinkle for msttcorefonts. It turns out that also need to point the wgetrc file in /etc at your proxy. 

You can insert

http_proxy = [http://ourproxy.yourdomain:yourport/](http://ourproxy.yourdomain:yourport/)

and you can get the fonts from inside the firewall

---

### Post by sav2005 on 2006-10-30
> **Dr. Nick said:**
> If i set the gnome proxy up and leave synaptic to "direct connect" it will go through the proxy on edgy, yours fails in that setup?

Yes, that's the whole problem.

---

### Post by sav2005 on 2006-10-30
> **nardis_Miles1 said:**
> You can  also edit the apt.conf file in /etc/apt 

inserting the lines:

Acquire
{
http
{
 Proxy "http://yourproxy.yourdomain:yourport";
 };
};

will get you there. There is another wrinkle for msttcorefonts. It turns out that also need to point the wgetrc file in /etc at your proxy. 

You can insert

http_proxy = [http://ourproxy.yourdomain:yourport/](http://ourproxy.yourdomain:yourport/)

and you can get the fonts from inside the firewall

I've played with that as well. Apt-get works if I export http_proxy but doesn't like the /etc/apt/apt.d/proxy solution and Synaptic does want any proxy setting but its' own! I had the same problem with Dapper but not Breezy. It may be specific to my company's proxy server.

---

