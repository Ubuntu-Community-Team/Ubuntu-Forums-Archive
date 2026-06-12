---
title: "Xfce error: &quot;could not look up internet address&quot;"
date: 2008-05-19
forum: General Help
---

### Post by cbraxton on 2008-05-19
I'm setting up a Ubuntu 8.04 server with xubuntu-desktop installed. (It needs to be administered by people new to Linux, so the GUI was installed.)

Sometime during the configuration, Xfce started giving an error message on startup that it "could not look up internet address" for the machine's hostname, asking to try again or continue anyway. (After continuing, everything works OK.)

What I've found via searches is that this is usually caused by the hostname not being in the /etc/hosts file. However, this is not the case here, the hosts file reads:

  127.0.0.1 localhost
  127.0.0.1 myserver

Also, the /etc/hostname file reads:

  myserver

Bind is installed, but not running. (We plan to set up local DNS later.) IPV6 is disabled by blacklisting the ipv6 module.

This is a very aggravating problem, every article I've read about it basically says that putting the hostname in the /etc/hosts file will "fix" it, but that just does not seem to be the case here.

Any other ideas? (I've spent a *lot* of time configuring this thing, reinstalling from scratch Windoze style, as a few of the articles I've found suggest, is not an option!)

Thanks for any help with this!

---

### Post by Jordanwb on 2008-05-19
Well 127.0.0.1 is your network device's loopback address. So what I think is that the network card is not getting an IP address from your DHCP device (most likely a router), or you didn't set up your interface correctly. It also could be that a cable isn't connected, or you don't have a network card.

Check the last two first, since they're the easiest.

---

### Post by cbraxton on 2008-05-19
> **Jordanwb said:**
> Well 127.0.0.1 is your network device's loopback address. So what I think is that the network card is not getting an IP address from your DHCP device (most likely a router), or you didn't set up your interface correctly. It also could be that a cable isn't connected, or you don't have a network card.


The network card has a static IP address assigned. I tried using that instead of the loopback address in /etc/hosts, but had the same result. (The articles I found suggesting the /etc/hosts fix all used the loopback address.)

Everything else works OK, the server can get to the internet, other systems on the network can get to Samba shares on the server, etc.

Interestingly, if I take out the "127.0.0.1 myserver" line from /etc/hosts, not only does the error message come up on Xfce startup, but also every time a command is run from a terminal. When that /etc/hosts line is put back in there are no more complaints from terminal sessions, but Xfce still complains upon startup.

---

### Post by cbraxton on 2008-05-19
Another data point -- from a terminal on the server, I can ping "myserver" by name and get a response. So it's not at all clear just what is causing Xfce to issue this error message.

---

### Post by plucky on 2008-05-19
Try these commands ```
route -n
``` and ```
cat /etc/resolv.conf
```

What are you using for the DNS server?

---

### Post by cbraxton on 2008-05-19
> **plucky said:**
> Try these commands

route -n  and  cat /etc/resolv.conf

What are you using for the DNS server?

The /etc/resolv.conf file contains a single line, "nameserver 192.168.20.1" (address of the internet router).

The router, a D-Link, acts as a forwarding or caching DNS server, with name resolution ultimately being performed by the ISP. There is no general problem with resolving internet host names. The server has bind9 installed, but it is currently deactivated. (Bind will be configured for caching and local DNS after the server is deployed.)

I'll check the routing table when I get back to the server in the morning, but the only thing I can think of that is modifying it is OpenVPN. (This adds a route to the VPN tunnel's subnet.)

---

### Post by cbraxton on 2008-05-20
The routing table is as follows:

```

Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.8.0.2        0.0.0.0         255.255.255.255 UH    0      0        0 tun0
192.168.20.0    0.0.0.0         255.255.255.0   U     0      0        0 eth0
10.8.0.0        10.8.0.2        255.255.255.0   UG    0      0        0 tun0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         192.168.20.1    0.0.0.0         UG    100    0        0 eth0

```

The 10.8.0.0 subnet is used by OpenVPN. Not sure why there is a 169.254.0.0 entry, but removing it does not affect the Xfce error message.

About the only other thing I can think of in the network setup that is the least bit unusual is that there are 2 onboard Broadcomm NICs that are disabled in /etc/rc.local via "ifconfig ethN down" (the motherboard BIOS has no provision for disabling them). An Intel PCI-E gigabit NIC is being used.

---

### Post by cbraxton on 2008-05-20
Having gotten nowhere in trying to resolve this problem, I downloaded the Xfce source code from xfce.org to take a closer look. After extracting it all and grepping for the error message, I found that it is issued from source file xfsm-dns.c. The relevant code is:

```

while (!check_for_dns ())
    {
      if (msgbox == NULL)
        {
          queryhostname (hostname, 256, TRUE);

          msgbox = gtk_message_dialog_new (NULL, 0,
                                           GTK_MESSAGE_WARNING,
                                           GTK_BUTTONS_NONE,
                                           _("Could not look up internet address for %s.\n"
                                             "This will prevent Xfce from operating correctly.\n"
                                             "It may be possible to correct the problem by adding\n"
                                             "%s to the file /etc/hosts on your system."),
                                           hostname, hostname);

          gtk_dialog_add_buttons (GTK_DIALOG (msgbox),
                                  _("Continue anyway"), RESPONSE_LOG_IN,
                                  _("Try again"), RESPONSE_TRY_AGAIN,
                                  NULL);

          xfsm_window_add_border (GTK_WINDOW (msgbox));
          xfce_gtk_window_center_on_monitor_with_pointer (GTK_WINDOW (msgbox));
        }

      gtk_dialog_set_default_response (GTK_DIALOG (msgbox), RESPONSE_TRY_AGAIN);

      response = xfsm_splash_screen_run (splash_screen, msgbox);
      if (response != RESPONSE_TRY_AGAIN)
        break;

      gtk_widget_hide (msgbox);
    }

  if (msgbox != NULL)
    gtk_widget_destroy (msgbox);
}

```

The error message is issued until either "check_for_dns()" returns a non-null value, or the user elects to continue despite the error. The check_for_dns() function is declared in the same source file:

```

check_for_dns (void)
{
#ifdef HAVE_GETADDRINFO
  struct addrinfo *result = NULL;
  struct addrinfo  hints;
#endif
  char   buffer[256];
  gchar *hostname;

  hostname = queryhostname (buffer, 256, FALSE);
  if (hostname == NULL)
    return FALSE;

#ifdef HAVE_GETADDRINFO
  bzero (&hints, sizeof (hints));
  hints.ai_socktype = SOCK_STREAM;
  hints.ai_flags = AI_CANONNAME;

  if (getaddrinfo (hostname, NULL, &hints, &result) != 0)
    return FALSE;

  if (g_ascii_strncasecmp (result->ai_canonname, hostname, 0) != 0)
    return FALSE;
#else
#ifdef HAVE_GETHOSTBYNAME
  if (gethostbyname (hostname) == NULL)
    {
      return FALSE;
    }
#endif
#endif

  return TRUE;
}

```

The problem is that here there be #ifdefs, and it is necessary to know what options the code was compiled with in Ubuntu to try to get an idea of where  this check is failing. To make things more complicated, the "queryhostname()" function is also declared in this source file and it too contains conditional #ifdef code:

```

queryhostname (gchar *buffer, gsize length, gboolean readable)
{
#ifdef HAVE_GETHOSTNAME
  if (gethostname (buffer, length) == 0)
    return buffer;
#else
  struct utsname utsname;
  if (uname (&utsname) == 0)
    {
      g_strlcpy (buffer, utsname.nodename, length);
      return buffer;
    }
#endif
  if (readable)
    {
      g_strlcpy (buffer, _("(Unknown)"), length);
      return buffer;
    }
  return NULL;
}

```

So there are several different possible places where this could be failing. It appears the next step would be to get the Ubuntu source code instead of the generic xfce.org code to figure out the compilation options, and maybe write a little test program using the same functions in order to figure out which of these checks is failing.

---

