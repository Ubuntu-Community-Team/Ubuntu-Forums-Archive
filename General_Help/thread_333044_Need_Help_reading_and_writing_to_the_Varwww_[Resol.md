---
title: "Need Help reading and writing to the Var/www [Resolved]"
date: 2007-01-06
forum: General Help
---

### Post by mikeylikesit on 2007-01-06
Hello, i am running Ubuntu "breezy badger" I am using apache2 for a webserver. I am not able to write or read in the var/www/apache2-default folder. I need to be able to put an index.html in there. I have looked on the forums and tried but with no luck. is it because i am using "breezy badger" Any help would be GREAT i dont know what i am doing wrong. my username is "mike" if that helps at all. 

THANKS!!

---

### Post by aysiu on 2007-01-06
```
sudo chown -R mike:mike /var/www
``` should do it.

You could also create a folder inside your home directory and symlink it there: ```
cd
mkdir web
sudo ln -s ~/web /var/www/web
```

---

### Post by mikeylikesit on 2007-01-06
THANK YOU SO MUCH :p

---

### Post by aysiu on 2007-01-06
> **mikeylikesit said:**
> THANK YOU SO MUCH :p
Which one worked for you? (Just curious)

---

### Post by mikeylikesit on 2007-01-07
sudo chown -R mike:mike /var/www

worked like a charm 
Thanks for all the help

---

### Post by wscheer on 2007-01-09
I am having the exact same problem but with dapper drake. I can't wait to get home and try this solution out.
i'll try sudo chown -R user:group /var/www/

I'm not sure how this happened when I set it up. I followed this online setup [http://www.howtoforge.com/perfect_setup_ubuntu_6.06](http://www.howtoforge.com/perfect_setup_ubuntu_6.06)

I just wanted an internal testing area so i skipped some of the installs that I did not were relevant. (probably my first mistake)

Just out of curiosity, what user should have ownership of /var/www/ ?
Is there any advantage/disadvantage to having a specific user have ownership?

I was skimming through looking for a solution to this problem and saw a few posts here about permissions to www. If i find any good ones, i'll append them to the end of this post since that will be my next mission.

---

### Post by Ramses de Norre on 2007-01-09
It's normally owned by www-data, the user which runs apache and which you can't login to.
This might be a security advantage and I just keep it like that here and write files to my server root with sudo..

---

