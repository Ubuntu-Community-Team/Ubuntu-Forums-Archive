---
title: "My Ubuntu 14.04 doesn´t boot - wn block(0,0)"
date: 2015-09-26
forum: General Help
---

### Post by ---r on 2015-09-26
Hello, I installed on my computer Windows 7 and Ubuntu following this guide: [http://ubuntuguide.org/wiki/Multiple_OS_Installation](http://ubuntuguide.org/wiki/Multiple_OS_Installation) The first Ubuntu release that I installed was 12.10 and I've been upgrading it until 14.04. My laptop charger was broken some time ago and my computer started to shut down suddenly. One day i couldn't shut down Linux properly and since then when I try to boot my computer i get the following message:

wn block(0,0)
[      0.656193]  CPU:   1  PID:   1  Comm:  swapper/0 Not tainted  3.13.0-63-generic  #103-
Ubuntu
[      0.656312]   Hardware  name:   Hewlett-Packard HP Pavilion dv6 Notebook PC/363E,
BIOS F.1E 05/19/2011
[      0.656427]   0000000000008001  ffff880139af5df0  ffffffff81723cc0 ffffffff81a3e
0d8
[      0.656928]    ffff880139af5e68    ffffffff8171cb43    ffffffff00000010 ffff880139af5
e78
[      0.657444]    ffff880139af5e18     ffffffff8171d66e    ffff880139af5e88 00000000000000
0cc
[      0.657963]   Call  Trace:
[      0.658068]     [<ffffffff81723cc0>]  dump_stack+0x45/0x56
[      0.658180]     [<ffffffff8171cb43>]  panic+0xc870x1d7
[      0.658293]     [<ffffffff8171d66e>]  ? printk+0x67/0x69
[      0.658401]     [<ffffffff81d3546a>]  mount_block_root+0x225/0x2b0
[      0.658516]     [<ffffffff81d35692>]  mount_root+0x53x56
[      0.658623]     [<ffffffff81d35801>]  prepare_namespace+0x16c/0x1a4
[      0.658735]     [<ffffffff81d3516e>]  kernel_init_freeable+0x1f3/0x200
[      0.658848]     [<ffffffff81d348e5>]   ? do_early_param+0x88/0x88
[      0.658956]     [<ffffffff81711ed0>]   ? rest_init+0x80/0x80
[      0.659063]     [<ffffffff81711ede>]   kernel_init+0xe/0x130
[      0.659173]     [<ffffffff817347e8>]  ret_from_fork+0x58/0x90
[      0.659293]     [<ffffffff81711ed0>]  ? rest_init+0x80/0x80

Can somebody help me????
Thanks

---

### Post by howefield on 2015-09-26
Thread moved to the "*General Help*" forum.

---

### Post by ---r on 2015-09-26
Sorry

---

### Post by Dreamer Fithp Apprentice on 2015-09-26
Presumably a grub problem. There are various grub fixing cd iso files available that would probably fix that, but if you don't have one, or can't conveniently get one and burn it on another machine, you'll probably have to use the same one you installed Ubuntu from, assuming you installed it from a CD. There are several ways to do that. If you haven't done a lot of tweaking you are loathe to lose, you could just reinstall over the old Ubuntu. If you don't want to do that look up "grub rescue" and similar search strings. You'll find there are programs you can install into the virtual filesystem of the live disk and then use to repair the hard disk installation. I forget which is which but you shouldn't have any trouble finding them with a search engine, such as startpage.com (like google without the evil). Some of them are programs you can install in the live system and some of them need to be on their own cd and I don't remember which is which offhand. Search for  rescatux or rescuatux (it is spelled inconsistently) and grub-fixer and similar terms.
And there is a third way in which you reinstall and update grub from the live disk. I think it involves chroot. I don't recall the details but I believe there is a tutorial on it on this site somewhere. Just search "how to repair grub".

---

### Post by ---r on 2015-10-11
Thanks for your help Dreamer. After following your advice of using a grub fixing cd i noticed that my system files were corrupted due to a dirty shut down. I reinstalled Ubuntu and everything is fine now. Take care

---

