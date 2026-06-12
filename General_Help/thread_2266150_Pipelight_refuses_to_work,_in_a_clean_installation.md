---
title: "Pipelight refuses to work, in a clean installation it does :("
date: 2015-02-20
forum: General Help
---

### Post by fkervin on 2015-02-20
Hi All,

I want yo access to a legal online streaming video content called "Yomvi". It uses Silverlight 5.0, so to be used on Linux it requires pipelight, an open-source project that allows to use Silverlight (among others) in Linux using wine.

My problem is that in my installation of xubuntu it does not work, It did when I installed pipelight, but since then I have install new software, I guess something in some point has made it fail. Now when I try to use it it gives a message saying **"Error in the player, please try later**".

 I have made a new (fresh) installation of xubuntu and then install pipelight in the way I did:

```
sudo add-apt-repository ppa:pipelight/stable
sudo apt-get update
sudo apt-get install --install-recommends pipelight-multi
sudo pipelight-plugin --update
sudo pipelight-plugin --enable silverlight5.0
```

Once firefox starts wine install Silverlight and works ok, even I've try to make:

```
sudo apt-get update
sudo apt-get upgrade
```

And it still works when I do this.

The problem is that I want to make it work in the other installation, it's a problem having to reinstall all programs again, and further this, it does not guarantee at all that it will fail again later.

Question is, why does it fail? and, how to fix?

I've try to remove firefox, uninstall pipelight-multi with "sudo apt-get remove" and "sudo apt-get purge" and removing ppa. Then I've make all the proccess again but it still fails, I don't know how actually remove silverlight and reinstall again, but in this way it doesn't work and a clear sign is that when I open firefox there is no silverlight installation as happends in the fresh install.

I hope someone can lend a hand.

Many thanks in advance and regards

---

### Post by SeijiSensei on 2015-02-20
Is Yomvi restricted to people living in Spain and connecting via Spanish ISPs?  Many video services have regional restrictions.

---

### Post by fkervin on 2015-02-20
Many thanks for your answer, SeijiSensei,

I'm connecting from Spain, and as I say, in my installation refuses to work while in a fresh installation it works ok.

I'd need a way to completely and really uninstall it, so i can install again as I do in the "fresh" installation.

Regards

---

