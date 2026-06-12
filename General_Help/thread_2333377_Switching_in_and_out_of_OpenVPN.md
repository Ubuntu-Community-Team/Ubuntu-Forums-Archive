---
title: "Switching in and out of OpenVPN"
date: 2016-08-09
forum: General Help
---

### Post by Robbyx on 2016-08-09
I subscribe to a OpenVPN account. 

Although it is easy to switch into the account, it is not easy to switch back to internet access without that layer because Ubuntu 14.04 looses the internet connection when I close the VPN connection. I have to restart Ubuntu and then run sudo service network-manager restart to get a non vpn internet connection.

In order to prevent data leakage I also use a utility called Vpnmon to drop the line if the vpn connection is dropped.
> Whenever your connections drops, vpnmon will either immediately disable your entire networking, or it will execute a custom command in case you provided one. The tool will also display a notification whenever it takes an action. 

I am wondering if it is vpnmon that is preventing the ordinary internet connection from restarting, but I do not know how to check that. Typing vpnmon into  terminal results in vpnmon not being known. 

No message comes up to say that the internet connection is being blocked when I switch out of the vpn. Here is the link for vpnmon:

 [http://lightrush.ndoytchev.com/random-1/vpnmon-avpnconnectionmonitorforlinux](http://lightrush.ndoytchev.com/random-1/vpnmon-avpnconnectionmonitorforlinux)

Any help in understanding what is happening would be very much appreciated

---

