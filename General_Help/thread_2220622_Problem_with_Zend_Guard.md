---
title: "Problem with Zend Guard"
date: 2014-04-28
forum: General Help
---

### Post by joob2 on 2014-04-28
Hello guys,

I have a problem with zend guard, I have a projecto with php, and this project requisite the Zend Guard, but this script to gives me a error:

[PHP]Error! Zend Guard or Zend Optimizer 3.3 or higher (required for ALL lincese types)![/PHP]

I have installed Zend Guard, but continues to give me the same error, oddly enough.

This is my php version:

[PHP]PHP 5.4.27-1+deb.sury.org~precise+1 (cli) (built: Apr  8 2014 10:08:18)
Copyright (c) 1997-2014 The PHP Group
Zend Engine v2.4.0, Copyright (c) 1998-2014 Zend Technologies
    with the ionCube PHP Loader v4.6.1, Copyright (c) 2002-2014, by ionCube Ltd., and
    with Zend Guard Loader v3.3, Copyright (c) 1998-2013, by Zend Technologies
    with Xdebug v2.2.3, Copyright (c) 2002-2013, by Derick Rethans[/PHP]

And this my php.ini with zend guard config:

[PHP]zend_extension=/usr/local/ioncube/ioncube_loader_lin_5.4.so
zend_extension=/usr/lib/php5/ZendGuardLoader.so
;zend_extension=/usr/lib/php5/20100525/xdebug.so

; Enables loading encoded scripts. The default value is On
zend_loader.enable=1
; Disable license checks (for performance reasons)
zend_loader.disable_licensing=0
; The Obfuscation level supported by Zend Guard Loader. The levels are detailed in the official Zend Guard Documentation. 0 - no obfuscation is enabled
zend_loader.obfuscation_level_support=0
; Path to where licensed Zend products should look for the product license. For more information on how to create a license file, see the Zend Guard User Guide
; zend_loader.license_path="[/PHP]

In other words, I have installed Zend Guard with PHP 5.4 and it works, but I'll check the Zend Guard, and gives me this:

> OK! The ZipArchive (zlib) is required!
**Error! Zend Guard or Zend Optimizer 3.3 or higher (required for ALL lincese types)!**
OK! Function "fopen" should be active!
OK! Function "curl" should be active!
OK! Function "scandir" should be active!
OK! MySQL 5 >= 5.5 is required!OK! PHP 5 >= 5.4 is required!
OK! Apache mod_rewrite is required!
OK! PHP GD2 >= 2.0 is required!
OK! PHP imagick is required (Recommended but is optional)!OK! Minimum memory limit of 512MB (You have 512 MB)!
OK! Enabled PHP5 mbstring!
OK! Enabled PHP5 DOMDocument!
OK! Register globals OFF!



I'm waiting for aid..


Regards,
Joob

---

