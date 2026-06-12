---
title: "Help with SQUID3 configuration."
date: 2014-08-14
forum: General Help
---

### Post by Rahul_Dev on 2014-08-14
Hi Guys,

I would like to configure my squid server which i have installed on Ubuntu 12.10 (32 Bit).
I am editing the config file so that i could use this single server for multiple outgoing ip address. I have got 6 ip from my provider for example. Now i have some configuration as given below.

# Squid normally listens to port 3128
http_port 67.xxx.108.128:3128 name=3128
http_port 67.xxx.108.79:3129 name=3129
http_port 67.xxx.108.80:3130 name=3130
http_port 67.xxx.108.221:3131 name=3131
http_port 208.xxx.34.154:3132 name=3132
http_port 208.xxx.34.32:3133 name=3133 

We just asked Squid to listen on sequential ports and to designate a  name for each inbound connection.  Now that we&#8217;ve named the inbound  connections, we can designate an ACL based on each inbound connection  name and assign an outgoing IP to each:

 acl tasty3128 myportname 3128 src 24.xxx.210.0/24
http_access allow tasty3128
tcp_outgoing_address 67.xxx.108.128 tasty3128

acl tasty3129 myportname 3129 src 24.xxx.210.0/24
http_access allow tasty3129
tcp_outgoing_address 67.xxx.108.79 tasty3129

acl tasty3130 myportname 3130 src 24.xxx.210.0/24
http_access allow tasty3130
tcp_outgoing_address 67.xxx.108.80 tasty3130

acl tasty3131 myportname 3131 src 24.xxx.210.0/24
http_access allow tasty3131
tcp_outgoing_address 67.xxx.108.221 tasty3131

acl tasty3132 myportname 3132 src 24.xxx.210.0/24
http_access allow tasty3132
tcp_outgoing_address 208.xxx.34.154 tasty3132

acl tasty3133 myportname 3133 src 24.xxx.210.0/24
http_access allow tasty3133
tcp_outgoing_address 208.xxx.34.32 tasty3133Questions.

1. can i use source as 0.0.0.0/24 so that from anywhere i can use.
2. Where do i put all this in squid config file ?? :(  :( does the location really matter ?
3. I will configure authentication later, but by default do i have to use any username/password in squid config file ?

I am trying to test it with Proxifier where.
1. I enter Ip address and port number.
2. Select https as protocol with no authentication and 
3. I click on check ( to test this proxy )
4. Volla!!!!!! and i fail miserably.
[B]
Logs from Proxifier[/B]

[03:38] Testing Started.
    Proxy Server
    Address:    23.249.161.xx:3130
    Protocol:    HTTPS
    Authentication: NO

[03:38] Starting: Test 1: Connection to the Proxy Server
[03:38] IP Address: 23.249.161.xx
[03:40] Could not connect to 23.249.161.xx:3130
    No connection could be made because the target computer actively refused it.
    Check your network connection and make sure that the proxy server address and port are correct.
    Also the error may indicate that the proxy server is down.
[03:40] Test failed.
[03:40] Testing Finished.

Can someone assist please what is that i am missing or even if i am doing it right ?

Regards.
Rahul

---

### Post by SeijiSensei on 2014-08-14
Proxying HTTPS requires some complicated configuration.  See the [SSLBump]("http://wiki.squid-cache.org/Features/SslBump") documentation for details.

I can't see any reason for multiple outbound addresses.  You give Squid a request, and it forwards it on for you.  What difference does it make which IP address it uses?  Just pick one and stick with that.

---

### Post by Rahul_Dev on 2014-08-14
I have my requirement of choosing different outgoing address.
I will check that document though. Thanks for assistance.

---

### Post by Rahul_Dev on 2014-08-14
I still need help with this outgoing ip thing.

---

### Post by SeijiSensei on 2014-08-16
> **Rahul_Dev said:**
> I still need help with this outgoing ip thing.

Until you explain what it is you want to do, I don't think any of us can help.  What application requires you to have multiple outbound addresses?  Give us an example of how the application would require one IP:port combination in one instance and a different one in another.

Just because you got a range of IPs from your ISP isn't a reason for this.  Usually you would be offering external services on the different IPs, like SMTP on one, HTTP on another, and HTTPS on a third.

You might be able to do what you want by launching separate instances of Squid each bound to a different IP:port combination.  As I said, I don't think Squid has any concept of sending different requests out different IP addresses.

---

