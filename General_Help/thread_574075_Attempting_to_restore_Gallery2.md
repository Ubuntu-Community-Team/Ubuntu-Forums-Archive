---
title: "Attempting to restore Gallery2"
date: 2007-10-12
forum: General Help
---

### Post by Arbiter on 2007-10-12
Hello all,

I've been trying to restore a Gallery2 setup to a new computer (my old server died). I have restored the images and mysql database, but I was wondering if it was possible to restore all of my old custom thumbnails? Also, when I attempt to edit an album I get the following message...any help would be greatly appreciated.

I know that this isn't a forum specifically for this program, but i've hit a wall, again, any help would be tremendously appreciated.


Error (ERROR_STORAGE_FAILURE)

* in modules/core/classes/GalleryStorage.class at line 476 (GalleryCoreApi::error)
* in modules/core/classes/Gallery.class at line 223 (GalleryStorage::search)
* in modules/imageblock/classes/ImageBlockHelper.class at line 763 (Gallery::search)
* in modules/imageblock/ImageBlockOption.inc at line 81 (ImageBlockHelper::getDisabledFlag)
* in modules/core/ItemEdit.inc at line 303 (ImageBlockOption::loadTemplate)
* in modules/core/ItemAdmin.inc at line 147 (ItemEditView::loadTemplate)
* in modules/core/classes/GalleryView.class at line 317 (ItemAdminView::loadTemplate)
* in main.php at line 386 (GalleryView::doLoadTemplate)
* in main.php at line 87
* in main.php at line 80

System Information
Gallery version 2.1.2
PHP version 5.2.1 apache2handler
Webserver Apache/2.2.3 (Ubuntu) PHP/5.2.1
Database mysql 5.0.38-Ubuntu_0ubuntu1-log
Toolkits SquareThumb, ImageMagick, NetPBM
Operating system Linux mercury 2.6.20-16-generic #2 SMP Sun Sep 23 19:50:39 UTC 2007 i686
Browser Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.8.1.6) Gecko/20061201 Firefox/2.0.0.6 (Ubuntu-feisty)

---

