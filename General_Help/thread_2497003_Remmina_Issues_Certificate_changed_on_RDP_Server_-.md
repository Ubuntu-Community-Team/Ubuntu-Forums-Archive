---
title: "Remmina Issues: Certificate changed on RDP Server - Now Remmina cannot connect"
date: 2024-04-19
forum: General Help
---

### Post by texpat on 2024-04-19
I connect to a remote Windows server via Remmina's RDP. This has worked flawlessly for years. Today, however, the server's certificate was renewed and Remmina couldn't connect any more.
I requested a new .rdp file which I imported into Remmina, but it still isn't connecting.
Ran Remmina with debug-mode and got this:

```
** (org.remmina.Remmina:22490): DEBUG: 17:00:27.001: proxy_type: (null)
** (org.remmina.Remmina:22490): DEBUG: 17:00:27.001: proxy_username: (null)
** (org.remmina.Remmina:22490): DEBUG: 17:00:27.001: proxy_password: (null)
** (org.remmina.Remmina:22490): DEBUG: 17:00:27.001: proxy_hostname: (null)
** (org.remmina.Remmina:22490): DEBUG: 17:00:27.001: proxy_port: 80
[17:00:26:773] [22490:22495] [INFO][com.freerdp.core] - freerdp_connect:freerdp_set_last_error_ex resetting error state
[17:00:26:773] [22490:22495] [INFO][com.freerdp.client.common.cmdline] - loading channelEx rdpdr
[17:00:26:773] [22490:22495] [INFO][com.freerdp.client.common.cmdline] - loading channelEx rdpsnd
[17:00:26:773] [22490:22495] [INFO][com.freerdp.client.common.cmdline] - loading channelEx cliprdr
[17:00:26:773] [22490:22495] [INFO][com.freerdp.client.common.cmdline] - loading channelEx drdynvc
[17:00:27:088] [22490:22495] [INFO][com.freerdp.primitives] - primitives autodetect, using optimized
[17:00:27:181] [22490:22495] [INFO][com.freerdp.core] - freerdp_tcp_connect:freerdp_set_last_error_ex resetting error state
[17:00:27:607] [22490:22495] [ERROR][com.freerdp.core] - rdg_establish_data_connection:freerdp_set_last_error_ex ERRCONNECT_ACCESS_DENIED [0x00020016]
libfreerdp returned code is 00020016
** (org.remmina.Remmina:22490): DEBUG: 17:00:27.837: Disconnect signal received on RemminaProtocolWidget

```

This is just the part I thought would be relevant - let me know if its not sufficient.
I'd really appreciate any insight into what is wrong and what I can do to make it connect again.
If any further info is necessary, please let me know.
System info: Xubuntu 20.04.6 LTS; Remmina 1.4.2 installed via apt
Thanks for reading
tx

---

### Post by ActionParsnip on 2024-04-19
Does this help
[https://blog.gpunktschmitz.com/posts/1083-certificate-error-when-initiating-a-rdp-session-using-remmina/](https://blog.gpunktschmitz.com/posts/1083-certificate-error-when-initiating-a-rdp-session-using-remmina/)

?

What are you dong on the Windows system that needs the full desktop session? There may be a sleeker solution to what you want to achieve

---

### Post by texpat on 2024-04-19
> Does this help

'fraid not. 

>   What are you dong on the Windows system that needs the full desktop session? There may be a sleeker solution to what you want to achieve 
I'm feeding a CMS with data. Corporate homebrew system. No way around it I'm afraid.

---

### Post by texpat on 2024-05-03
bump

Any ideas?

---

