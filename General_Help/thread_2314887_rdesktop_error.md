---
title: "rdesktop error"
date: 2016-02-24
forum: General Help
---

### Post by joker535 on 2016-02-24
I just upgraded from an older Mint 16 install to a fresh Ubuntu 15.10 install. The included older version of rdesktop worked just fine on the Mint 16 install and continues to work fine conecting tot hat same server using another machine I have with the same version of Mint 16. Unfortunately it will not connect to my Windows server on the new Ubuntu 15.10 install. It fails with this error:

[I]ERROR: tcp_tls_get_server_pubkey: SSL_get_peer_certificate() failed
ERROR: CredSSP: Initialize failed, do you have correct kerberos tgt initialized ?
Failed to connect, CredSSP required by server.[/I]

I have followed every item I could find on google search and gotten no resolution. 

Any ideas?

Thanks

---

### Post by allegfede on 2016-06-10
got same error ... have you solved?

---

### Post by joker535 on 2016-06-13
> **allegfede said:**
> got same error ... have you solved?

Nope. RDP works fine from any other Windows box and works fine from the Jump Desktop RDP software on my android phone. It just will not work from Ubuntu/RDesktop.

---

### Post by joker535 on 2016-09-05
I upgraded to 16.04.01 LTS and exactly the same issue is still there (RDesktop is still 1.8.3 so this is no surprise). 

I get this:

Autoselected keyboard map en-us
ERROR: tcp_tls_get_server_pubkey: SSL_get_peer_certificate() failed
ERROR: CredSSP: Initialize failed, do you have correct kerberos tgt initialized ?
Failed to connect, CredSSP required by server.

I believe RDesktop is trying to use a cypher suite that is not available on a Windows server that has been modified for PCI scan compliance.
I searched for the error and found this url: [https://sourceforge.net/p/rdesktop/mailman/message/29409257/](https://sourceforge.net/p/rdesktop/mailman/message/29409257/)

I searched that page for the error and found this:

[I]+/* Get public key from server of TLS 1.0 connection */
+RD_BOOL
+tcp_tls_get_server_pubkey(STREAM s)
+{
+	X509 *cert = NULL;
+	EVP_PKEY *pkey = NULL;
+
+	s->data = s->p = NULL;
+	s->size = 0;
+
+	if (g_ssl == NULL)
+		goto out;
+
+	cert = SSL_get_peer_certificate(g_ssl);
+	if (cert == NULL)
+	{
+		error("**tcp_tls_get_server_pubkey: SSL_get_peer_certificate() failed**\n");
+		goto out;
+	}
+
+	pkey = X509_get_pubkey(cert);
+	if (pkey == NULL)
+	{
+		error("tcp_tls_get_server_pubkey: X509_get_pubkey() failed\n");
+		goto out;
+	}[/I]

I suspect rdesktop is tying to use some out of date cypher suite to do this. 

I tested Remmina and it did not work at all. 

Anyone have any other suggestions?

---

### Post by joker535 on 2016-09-05
I found a way around the remmina issue. I prefer RDesktop and use it for all my other RDP connections but remmina will do until I get RDesktop figured out. 

Open a terminal and run these:

sudo apt-add-repository ppa:remmina-ppa-team/remmina-next
sudo apt-get update
sudo apt-get install remmina remmina-plugin-rdp libfreerdp-plugins-standard

Once its done run this:

sudo killall remmina

I can now connect to that one server using remmina. 

Its better than nothing.

---

### Post by TheFu on 2016-09-05
Only have a Win7 machine that I RDP into from Ubuntu.  Remember having to enable some legacy support  on Windows to get it working years ago. It still works, but since it is only for home use and only used on the LAN, I wasn't worried about the weaker settings.  Never changed the settings back and don't recall what they were today. Sorry.

[https://technet.microsoft.com/en-us/library/cc770833(v=ws.11).aspx](https://technet.microsoft.com/en-us/library/cc770833(v=ws.11).aspx) might be related. Knowing the options and being allowed to change them are 2 different issues.

---

### Post by mysilverkey on 2017-04-11
Hi All,
Remmina worked for me. Good software. Thank you.

---

