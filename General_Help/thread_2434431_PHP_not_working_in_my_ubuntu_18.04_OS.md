---
title: "PHP not working in my ubuntu 18.04 OS"
date: 2020-01-06
forum: General Help
---

### Post by shan2naruto on 2020-01-06
hi,
yesterday night after working in netbeans and browser for php i closed my laptop and went to sleep. Today morning when i try to work with my projects in browser it is not working i deducted it to be a php problem as it happening in my previous installation and i feared a data breach and reinstalled the OS. And now i see the same problem again. 
problems:
when i try to login to my project it is not logging in the same probblem i faced with the previous installation. How do i troubleshoot this problem in ubuntu 18.04.03 as i'm able to use only phpmyadmin

> gowri@gowri:~$ php --version
PHP 7.2.24-0ubuntu0.18.04.1 (cli) (built: Oct 28 2019 12:07:07) ( NTS )
Copyright (c) 1997-2018 The PHP Group
Zend Engine v3.2.0, Copyright (c) 1998-2018 Zend Technologies
    with Zend OPcache v7.2.24-0ubuntu0.18.04.1, Copyright (c) 1999-2018, by Zend Technologies


---

### Post by ponef on 2020-01-29
> **shan2naruto said:**
> hi,
yesterday night after working in netbeans and browser for php i closed my laptop and went to sleep. Today morning when i try to work with my projects in browser it is not working i deducted it to be a php problem as it happening in my previous installation and i feared a data breach and reinstalled the OS. And now i see the same problem again. 
problems:
when i try to login to my project it is not logging in the same probblem i faced with the previous installation. How do i troubleshoot this problem in ubuntu 18.04.03 as i'm able to use only phpmyadmin

Hi buddy, did you get any working solution yet to this? If yes would you mind briefing more into it.

Regards,
Noel Smith [Tutuapp](https://dltutuapp.com/tutuapp-download/) [ShowBox](https://showbox.run/) [Kodi](https://kodi.software/)

---

### Post by mastablasta on 2020-01-30
there is not much to go on. not working does not provide a good description. 
Suggestions on how to get your support questions answered as quickly as possible: [https://ubuntuforums.org/showthread.php?t=1422475](https://ubuntuforums.org/showthread.php?t=1422475)

also if PHP is the issue then PHP forums might be better.

finally, i suggest you do this kind of thing in a virtualbox or similar VM environment that allows you to take snapshots. if something get's broken, you can just restore previous snapshot. in takes about 45 seconds to restore it on my 15 year old single core PC.

another option is BTRFS file system, but that's an overkill to just have snapshots available for server software and development.

---

