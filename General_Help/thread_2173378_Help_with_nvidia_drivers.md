---
title: "Help with nvidia drivers"
date: 2013-09-09
forum: General Help
---

### Post by stroller-tb on 2013-09-09
Hello,

I'm using a Nvidia GTX 480 to do some tests with cuda and a Quadro FX 570 to run X.
As my display was freexing, I tried to update the drivers using one that I downloades from Nvidia site. When I did this, I could no longer see anything. So I've removed all nvidia settings and try to reinstall some driver using apt-get.
My screen back, but I don't have the top menu bar or the lateral menu app. Can anyone help me?

---

### Post by pqwoerituytrueiwoq on 2013-09-09
sounds like compiz is not working due to lack of driver
if you installed from nvidia's site use [FONT=courier new]sudo nvidia-installer --uninstall[/FONT] to remove it
ctrl+alt+f1 for terminal login
output of [FONT=courier new]lspci -vv | grep "VGA com" -A12[/FONT] should be helpful in particular the **Kernel driver in use** line
install the driver via software sources ([FONT=courier new]software-properties-gtk[/FONT])
[[img]http://www.zimagez.com/miniature/screenshot-09092013-101437am.php[/img]](http://www.zimagez.com/zimage/screenshot-09092013-101437am.php)

---

