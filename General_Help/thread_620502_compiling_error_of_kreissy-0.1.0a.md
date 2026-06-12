---
title: "compiling error of kreissy-0.1.0a"
date: 2007-11-22
forum: General Help
---

### Post by of_darkness on 2007-11-22
> error: po: No such file or directory

the relevent part of the install script:*> import kdedistutils
 kdedistutils.setup(name="kreissy",
*   version="0.1.0a",
*   author="Marcos Dione",
*   author_email="mdione@grulic.org.ar",
*   url="",
*   min_kde_version = "3.0.0",
*   min_qt_version = "3.0.0",
*   license = "GPL2",
*   # application_data = ['src/kdeutility.py','src/KDEUtilityDialogUI.ui'],
*   application_data = ['src/kress.py'],
*   executable_links = [('kress','kress.py')],
*   docbooks = [ ('doc/en','en') ],
*   i18n = ('po',['src']) )

 i can gather that po is somthing related to translations and gettext but i guess with my nonexistent knowladge of programing that it calls for my internationalisation there in something in the src that exist in the kreissy directory..*

So my question is can i modify the script to work or do i nead 2 install or configure some thing?*

downloaded the package from [http://www.kde-apps.org/content/show.php/kReiSSy?content=66835](http://www.kde-apps.org/content/show.php/kReiSSy?content=66835)

---

