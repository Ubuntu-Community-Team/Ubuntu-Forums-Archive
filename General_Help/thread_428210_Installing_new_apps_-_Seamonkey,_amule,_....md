---
title: "Installing new apps - Seamonkey, amule, ..."
date: 2007-04-30
forum: General Help
---

### Post by FizzBuntu on 2007-04-30
Ok, here it is
Got Ubuntu feisty fawn install nicely, no prob at all, all softwares and internet connection are working fine.
Now I'd like to customize a little bit the apps.
I'd like to use Seamonkey instaead of firefox and thunderbird, so I used this [http://monkeyblog.org/ubuntu/installing/#]("http://monkeyblog.org/ubuntu/installing/#") to try to install it, but obviously, that was for dapper drake, and I just can't find the damn Seamonkey, or any other softwares i'd like to use....

any clues ?

Finaly found amule...

---

### Post by Sef on 2007-04-30
> Got Ubuntu feisty fawn install nicely, no prob at all, all softwares and internet connection are working fine.
Now I'd like to customize a little bit the apps.
I'd like to use Seamonkey instaead of firefox and thunderbird, so I used this [http://monkeyblog.org/ubuntu/installing/#](http://monkeyblog.org/ubuntu/installing/#) to try to install it, but obviously, that was for dapper drake, and I just can't find the damn Seamonkey, or any other softwares i'd like to use....


Basically Feisty will be the same as Dapper.  Just those directions.

First check and see if it is in the following:

1)Add/Remove (Applications > Add/Remove > Search)

2) Synaptic (System > Administration > Synaptic Package Manager)

---

### Post by FizzBuntu on 2007-04-30
OK, found wine, amule nd a couple of other stuff, but still no sign of seamonkey !!!
plus, now the add/remove thing asks for the Feisty fawn cd ...

---

### Post by foug on 2007-04-30
sudo apt-get install seamonkey-mozilla (maybe mozilla-seamonkey?)

something like that...

---

### Post by FizzBuntu on 2007-04-30
OK, I tried both and got the answer that he can't find the package...

---

### Post by foug on 2007-04-30
You might need to add some third party repositories. I installed it once through terminal and sudo apt-get install seamonkey-mozilla was what I did. If not it was something similar. I stopped using SeaMonkey and started using Opera though.

---

### Post by FizzBuntu on 2007-05-01
ok, how do you add 3rd party repositories ?

I've tried downloading and installing Seamonkey from the  mozilla website but it has to be launch as root to create and install well, so ...

---

### Post by foug on 2007-05-03
you can use sudo -command- for whatever it tells oyu to do as root i think

---

### Post by FizzBuntu on 2007-05-10
yup, not easy, but it finally worked, thx

---

