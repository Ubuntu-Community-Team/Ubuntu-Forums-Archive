---
title: "SquidGuard not allowing an ip to be excluded"
date: 2014-02-25
forum: General Help
---

### Post by sean35 on 2014-02-25
Hi all,

Please can you help me with my squidguard configuration.

For example I'm trying to block an entire range ( 192.168.168.0/24) from browsing porn

By doing that I have the following:-

src bombelaop {
ip 		192.168.168.0/24 
}


acl{
bombelaop {
		pass !porn all
		redirect [http://192.168.168.156/blocked.html?clientaddr=%a+clientname=%n+clientident=%i+srcclass=%s+targetclass=%t+url=%u](http://192.168.168.156/blocked.html?clientaddr=%a+clientname=%n+clientident=%i+srcclass=%s+targetclass=%t+url=%u)
	}
}

That is working 100% fine however I'm trying to then allow just myself to view porn (This is for demo purposes, I'm not actually trying to view porn lol :)   )

So I added this configuration:-

src allowed {
ip 192.168.168.171
}

alc {
allowed {
		pass none
		redirect [http://192.168.168.156/blocked.html?clientaddr=%a+clientname=%n+clientident=%i+srcclass=%s+targetclass=%t+url=%u](http://192.168.168.156/blocked.html?clientaddr=%a+clientname=%n+clientident=%i+srcclass=%s+targetclass=%t+url=%u)
	}




}

For some strange reason It's not excluding me? Is this even possible? Please help!

---

### Post by ukfromit on 2014-03-13
src bomelaop {
                 ip      192.168.168.171
}
##default acl should be like this

acl {
           bombeloap {
                       pass all 
                          }
            default {
                     pass !porn all 
                     redirect [http://192.168.168.156/blocked.html](http://192.168.168.156/blocked.html)
                     }
}

---

