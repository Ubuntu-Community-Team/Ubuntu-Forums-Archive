---
title: "must enter password on every boot"
date: 2023-12-04
forum: General Help
---

### Post by jgw on 2023-12-04
I keep getting "The login keyring did not get unlocked when you logged into your computer"  My login password is "greg".  I checked my settings and its as it should be (I thought).

I then looked around and found that I had some password stuff which I could do stuff with.  One was /login/share/keyrings (where login.keyring and user.keystore reside.  The other was /activities/passwords and keys.  I went to these places and found more stuff:
{'username': <'greg'>, 'password': <'XUDEsWIpkezE'>}  (twice) and:

{'macaroon': <'MDAxM2xvY2F0aW9uIHNuYXBkCjAwMTFpZGVudGlmaWVyIDEKMDAyZnNpZ25hdHVyZSARDWIc35n6a2gD2rF0ewStVTeufo_9Ww2l27J5XD6nnwo'>, 'discharges': <'[]'>, 'livepatch': <'7e2f2470b2694be0a93222d69b44fb4a'>}

{'macaroon':
 <'MDAxM2xvY2F0aW9uIHNuYXBkCjAwMTFpZGVudGlmaWVyIDEKMDAyZnNpZ25hdHVyZSARDWIc35n6a2gD2rF0ewStVTeufo_9Ww2l27J5XD6nnwo'>, 'discharges': <'[]'>, 'livepatch': <'7e2f2470b2694be0a93222d69b44fb4a'>}
  and then the same thing again.
  
  I know, this is a mess and I am, obviously, confused.  I saw the macaroon stuff and figured it was time to ask somebody what I should do (if anything)  I would like to get rid of entering the login but perhaps I should just leave everything alone.  

I should add that I also did "sudo apt-get update && sudo apt upgrade -y"  Just to make sure everything was dandy.  It did stuff but there were no problems.

system-info.txt    [https://pastebin.ubuntu.com/p/FYG7Q6Zvmf/](https://pastebin.ubuntu.com/p/FYG7Q6Zvmf/)

  
  Thoughts?

---

### Post by MAFoElffen on 2023-12-06
Here you go: [https://askubuntu.com/questions/867/how-can-i-stop-being-prompted-to-unlock-the-default-keyring-on-boot](https://askubuntu.com/questions/867/how-can-i-stop-being-prompted-to-unlock-the-default-keyring-on-boot)

---

### Post by jgw on 2023-12-07
Thanks for the reply!

I gotta tell you, I have already taken a look at that one.  Basically, I think I will just live with it.  Its the only machine that requires it and its not a big deal.  

Went to Olympia last weekend and got sleeted on!  Found that Olympia has some stores that are lunatic at the very least.  Educational!

---

