---
title: "Somethings wrong with my sources.list"
date: 2007-12-12
forum: General Help
---

### Post by Afkpuz on 2007-12-12
Hi.  When running synaptec, I get the following error.

E: Type '<!DOCTYPE' is not known on line 1 in source list /etc/apt/sources.list.d/springproject.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.



  Here is my sources.list



```

deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ gutsy main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu/ gutsy universe
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy universe
deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ gutsy multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy multiverse
deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb http://archive.canonical.com/ubuntu gutsy partner
# deb-src http://archive.canonical.com/ubuntu gutsy partner

deb http://security.ubuntu.com/ubuntu gutsy-security main restricted
deb-src http://security.ubuntu.com/ubuntu gutsy-security main restricted
deb http://security.ubuntu.com/ubuntu gutsy-security universe
deb-src http://security.ubuntu.com/ubuntu gutsy-security universe
deb http://security.ubuntu.com/ubuntu gutsy-security multiverse
deb-src http://security.ubuntu.com/ubuntu gutsy-security multiverse



```


P.S., this problem arose when I tried to add the repo for that new Total Anihilation game, Spring.  I was following this pages instructions.  
[http://spring.clan-sy.com/wiki/SetupGuide#Ubuntu](http://spring.clan-sy.com/wiki/SetupGuide#Ubuntu)

I don't know enough about the sources.list to see what is wrong with line 1.  Can anyone help?  I think that a fresh install sources.list would fix it, so if someone could post that, that would be great.  Thanks

---

### Post by geirha on 2007-12-12
I'm betting /etc/apt/sources.list.d/springproject.list has a 404-html page in it. You've probably mistyped something on the wget command, or the gutsy.list was temporarily unavailable at the moment you ran the command. Running the wget command again should fix it.

---

### Post by aysiu on 2007-12-12
Post the output of this command: ```
cat /etc/apt/sources.list.d/springproject.list
```

---

### Post by Afkpuz on 2007-12-12
<!DOCTYPE html
        PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN"
         "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">
<html xmlns="http://www.w3.org/1999/xhtml" lang="en-US" xml:lang="en-US">
<head>
<title>Barracuda Web Filter</title>
<meta http-equiv="Content-Type" content="text/html; charset=iso-8859-1" />
</head>
<body>
<span id="redir_msg" style="display: none"><p>Redirecting to Barracuda Web Filter...</p></span><script x-barracuda="1" language="JavaScript">
if (0) {
  document.write('<div style="border: 1px dotted red; padding: 2px; font-family: sans; font-size: 12px; color: black; background-color: white">This portion of the requested page has been blocked.<br /><a target="_top" href="http://172.27.72.27/web/login?_bcsp=1&amp;_bceq=U2FsdGVkX19_WltLYk4H4va6p_IGQq6uJD7aobGyv6BPtWVMcDxLjKpYfyVy3NlEk5Md8gg7LYp6XWGWFB9K_9YYZHmbe6_mvfXgmiJWtWPP9Qg6RoIrmSiMAJm1M69L2oRsDxTq_-g4hn7YEVKoYglp9Rs_Hl8J4jYHbSIOmqYZ2raM5MP2nltUn2RNJo2-XkXmNglYCQuU8filVPs8LnhIrZ1BtKlNMjD9iWEAx8mFP5aoUcVd6Ep4Ph77muFh7eUYSFDYggEGXnNzF25KI4T1g5tw-9cOG46B8uqoVT3Dk6zIypGACGQ8QSzK4R2dIgrFdcR4s6sUliTdU_8dkY2WTNi4vE69c4g7-E0-ua1KkgcAd2kVA4B9u-AFhRFuAn4YP6LJsibYff4HAnjuGipNGZd1MVu5zwyw15T9TgcFh7ZZq8aTpnfh5_v8V0XfZyX0FJFo7YEb2t5C3JKL7hO5JXNNnAChAEG7H2k4_6KSsDy_39V-paJfz_uAtnd_WCdYnsC1_YWzD3GHak7adyVQnNOni_ocaYP61V9mQcjHLsJoBC36ycnah4ABElkOIljUrcPKVlZWQAUqbUSfTlgIkeoDq2eYeCwvk8hBuRMP4zBOR3gB4Q..">Click here for details.</a></div>');
} else {
  if (!0) {
    var toploc;
    try { toploc = top.document.location }
    catch (err) { toploc = err };
    if ((toploc == document.location)) {
      document.getElementById('redir_msg').style.display = 'inline';
      if (location.replace) {
        location.replace('http://172.27.72.27/web/login?_bcsp=1&_bceq=U2FsdGVkX19_WltLYk4H4va6p_IGQq6uJD7aobGyv6BPtWVMcDxLjKpYfyVy3NlEk5Md8gg7LYp6XWGWFB9K_9YYZHmbe6_mvfXgmiJWtWPP9Qg6RoIrmSiMAJm1M69L2oRsDxTq_-g4hn7YEVKoYglp9Rs_Hl8J4jYHbSIOmqYZ2raM5MP2nltUn2RNJo2-XkXmNglYCQuU8filVPs8LnhIrZ1BtKlNMjD9iWEAx8mFP5aoUcVd6Ep4Ph77muFh7eUYSFDYggEGXnNzF25KI4T1g5tw-9cOG46B8uqoVT3Dk6zIypGACGQ8QSzK4R2dIgrFdcR4s6sUliTdU_8dkY2WTNi4vE69c4g7-E0-ua1KkgcAd2kVA4B9u-AFhRFuAn4YP6LJsibYff4HAnjuGipNGZd1MVu5zwyw15T9TgcFh7ZZq8aTpnfh5_v8V0XfZyX0FJFo7YEb2t5C3JKL7hO5JXNNnAChAEG7H2k4_6KSsDy_39V-paJfz_uAtnd_WCdYnsC1_YWzD3GHak7adyVQnNOni_ocaYP61V9mQcjHLsJoBC36ycnah4ABElkOIljUrcPKVlZWQAUqbUSfTlgIkeoDq2eYeCwvk8hBuRMP4zBOR3gB4Q..');
      } else {
        document.location = 'http://172.27.72.27/web/login?_bcsp=1&_bceq=U2FsdGVkX19_WltLYk4H4va6p_IGQq6uJD7aobGyv6BPtWVMcDxLjKpYfyVy3NlEk5Md8gg7LYp6XWGWFB9K_9YYZHmbe6_mvfXgmiJWtWPP9Qg6RoIrmSiMAJm1M69L2oRsDxTq_-g4hn7YEVKoYglp9Rs_Hl8J4jYHbSIOmqYZ2raM5MP2nltUn2RNJo2-XkXmNglYCQuU8filVPs8LnhIrZ1BtKlNMjD9iWEAx8mFP5aoUcVd6Ep4Ph77muFh7eUYSFDYggEGXnNzF25KI4T1g5tw-9cOG46B8uqoVT3Dk6zIypGACGQ8QSzK4R2dIgrFdcR4s6sUliTdU_8dkY2WTNi4vE69c4g7-E0-ua1KkgcAd2kVA4B9u-AFhRFuAn4YP6LJsibYff4HAnjuGipNGZd1MVu5zwyw15T9TgcFh7ZZq8aTpnfh5_v8V0XfZyX0FJFo7YEb2t5C3JKL7hO5JXNNnAChAEG7H2k4_6KSsDy_39V-paJfz_uAtnd_WCdYnsC1_YWzD3GHak7adyVQnNOni_ocaYP61V9mQcjHLsJoBC36ycnah4ABElkOIljUrcPKVlZWQAUqbUSfTlgIkeoDq2eYeCwvk8hBuRMP4zBOR3gB4Q..';
      }
    } else {
      document.write('<div style="border: 1px dotted red; padding: 2px; font-family: sans; font-size: 12px; color: black; background-color: white">This portion of the requested page has been blocked.<br /><a target="_top" href="http://172.27.72.27/web/login?_bcsp=1&amp;_bceq=U2FsdGVkX19_WltLYk4H4va6p_IGQq6uJD7aobGyv6BPtWVMcDxLjKpYfyVy3NlEk5Md8gg7LYp6XWGWFB9K_9YYZHmbe6_mvfXgmiJWtWPP9Qg6RoIrmSiMAJm1M69L2oRsDxTq_-g4hn7YEVKoYglp9Rs_Hl8J4jYHbSIOmqYZ2raM5MP2nltUn2RNJo2-XkXmNglYCQuU8filVPs8LnhIrZ1BtKlNMjD9iWEAx8mFP5aoUcVd6Ep4Ph77muFh7eUYSFDYggEGXnNzF25KI4T1g5tw-9cOG46B8uqoVT3Dk6zIypGACGQ8QSzK4R2dIgrFdcR4s6sUliTdU_8dkY2WTNi4vE69c4g7-E0-ua1KkgcAd2kVA4B9u-AFhRFuAn4YP6LJsibYff4HAnjuGipNGZd1MVu5zwyw15T9TgcFh7ZZq8aTpnfh5_v8V0XfZyX0FJFo7YEb2t5C3JKL7hO5JXNNnAChAEG7H2k4_6KSsDy_39V-paJfz_uAtnd_WCdYnsC1_YWzD3GHak7adyVQnNOni_ocaYP61V9mQcjHLsJoBC36ycnah4ABElkOIljUrcPKVlZWQAUqbUSfTlgIkeoDq2eYeCwvk8hBuRMP4zBOR3gB4Q..">Click here for details.</a></div>');
    }
  }
}
</script><noscript><p>JavaScript has been disabled in your browser.</p> <p><a href="http://172.27.72.27/web/login?_bcsp=1&amp;_bceq=U2FsdGVkX19_WltLYk4H4va6p_IGQq6uJD7aobGyv6BPtWVMcDxLjKpYfyVy3NlEk5Md8gg7LYp6XWGWFB9K_9YYZHmbe6_mvfXgmiJWtWPP9Qg6RoIrmSiMAJm1M69L2oRsDxTq_-g4hn7YEVKoYglp9Rs_Hl8J4jYHbSIOmqYZ2raM5MP2nltUn2RNJo2-XkXmNglYCQuU8filVPs8LnhIrZ1BtKlNMjD9iWEAx8mFP5aoUcVd6Ep4Ph77muFh7eUYSFDYggEGXnNzF25KI4T1g5tw-9cOG46B8uqoVT3Dk6zIypGACGQ8QSzK4R2dIgrFdcR4s6sUliTdU_8dkY2WTNi4vE69c4g7-E0-ua1KkgcAd2kVA4B9u-AFhRFuAn4YP6LJsibYff4HAnjuGipNGZd1MVu5zwyw15T9TgcFh7ZZq8aTpnfh5_v8V0XfZyX0FJFo7YEb2t5C3JKL7hO5JXNNnAChAEG7H2k4_6KSsDy_39V-paJfz_uAtnd_WCdYnsC1_YWzD3GHak7adyVQnNOni_ocaYP61V9mQcjHLsJoBC36ycnah4ABElkOIljUrcPKVlZWQAUqbUSfTlgIkeoDq2eYeCwvk8hBuRMP4zBOR3gB4Q..">Proceed to detail/login page</a></p></noscript>
</body>
</html>

---

### Post by aysiu on 2007-12-12
Yeah, you appear to have some kind of webpage as your source. That ain't right.

---

### Post by Afkpuz on 2007-12-12
How to fix?

---

### Post by aysiu on 2007-12-12
> **Afkpuz said:**
> How to fix?
Paste these commands into the terminal: ```
sudo rm /etc/apt/sources.list.d/springproject.list
wget -q http://buildbot.no-ip.org/~yokozar/apt/387EE263.gpg -O- | \ sudo apt-key add -
sudo wget http://buildbot.no-ip.org/~yokozar/apt/sources.list.d/gutsy.list \ -O /etc/apt/sources.list.d/springproject.list
sudo apt-get update
sudo apt-get install spring -y
sudo apt-get install spring-lobby-springlobby -y
``` I the error might have come about because of what this warning talks about: > Those lines are long and split to fit on this page, you can copy-paste this to your terminal as is, as long as you copy all lines and not just one. The lines wrap on that page. Shouldn't be an issue on the forums, though, since the lines don't wrap here. So you can go ahead and copy and paste line by line.

---

### Post by Afkpuz on 2007-12-12
That fixed the synaptec problem, but the the wget line does not work.  Says "No valid OpenPGP data found".  Is it just something wrong on their side?

---

### Post by aysiu on 2007-12-12
> **Afkpuz said:**
> That fixed the synaptec problem, but the the wget line does not work.  Says "No valid OpenPGP data found".  Is it just something wrong on their side?
It would seem that way.

Technically, you don't need a GPG key in order to install the software, if you ignore the warnings about not being able to verify the download.

---

