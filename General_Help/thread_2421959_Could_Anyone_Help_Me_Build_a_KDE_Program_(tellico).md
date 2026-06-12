---
title: "Could Anyone Help Me Build a KDE Program (tellico) for 18.04 LTS?"
date: 2019-06-29
forum: General Help
---

### Post by rebeltaz on 2019-06-29
Can anyone here help me build tellico from source under a gnome environment? I am running Ubuntu 18.04 LTS and the version of tellico in the repositories is always out of date. Right now I am stuck at 3.1.2. I know how to build packages aimed at gnome, but not kde. I really like this program, but not being able to use the bardcode scanner (I guess out of date sources?) is really a pain! z

I installed cmake and ran it but it keeps giving me errors I do not understand:

```

 cmake .. -DCMAKE_INSTALL_PREFIX=`kf5-config --prefix`
CMake Deprecation Warning at CMakeLists.txt:12 (CMAKE_POLICY):
  The OLD behavior for policy CMP0028 will be removed from a future version
  of CMake.

  The cmake-policies(7) manual explains that the OLD behaviors of all
  policies are deprecated and that a policy should be set to OLD only under
  specific short-term circumstances.  Projects should be ported to the NEW
  behavior and not rely on setting a policy to OLD.


-- Installing in the same prefix as Qt, adopting their path scheme.
-- Looking for __GLIBC__
-- Looking for __GLIBC__ - found
-- Performing Test _OFFT_IS_64BIT
-- Performing Test _OFFT_IS_64BIT - Success
-- Performing Test HAVE_DATE_TIME
-- Performing Test HAVE_DATE_TIME - Success
-- Looking for strlwr
-- Looking for strlwr - not found
-- Looking for strupr
-- Looking for strupr - not found
-- Could NOT find KF5Archive (missing: KF5Archive_DIR)
-- Could NOT find KF5Archive: found neither KF5ArchiveConfig.cmake nor kf5archive-config.cmake 
-- Could NOT find KF5Codecs (missing: KF5Codecs_DIR)
-- Could NOT find KF5Codecs: found neither KF5CodecsConfig.cmake nor kf5codecs-config.cmake 
-- Could NOT find KF5Config (missing: KF5Config_DIR)
-- Could NOT find KF5Config: found neither KF5ConfigConfig.cmake nor kf5config-config.cmake 
-- Could NOT find KF5ConfigWidgets (missing: KF5ConfigWidgets_DIR)
-- Could NOT find KF5ConfigWidgets: found neither KF5ConfigWidgetsConfig.cmake nor kf5configwidgets-config.cmake 
-- Could NOT find KF5CoreAddons (missing: KF5CoreAddons_DIR)
-- Could NOT find KF5CoreAddons: found neither KF5CoreAddonsConfig.cmake nor kf5coreaddons-config.cmake 
-- Could NOT find KF5Crash (missing: KF5Crash_DIR)
-- Could NOT find KF5Crash: found neither KF5CrashConfig.cmake nor kf5crash-config.cmake 
-- Could NOT find KF5DocTools (missing: KF5DocTools_DIR)
-- Could NOT find KF5DocTools: found neither KF5DocToolsConfig.cmake nor kf5doctools-config.cmake 
-- Could NOT find KF5GuiAddons (missing: KF5GuiAddons_DIR)
-- Could NOT find KF5GuiAddons: found neither KF5GuiAddonsConfig.cmake nor kf5guiaddons-config.cmake 
-- Could NOT find KF5IconThemes (missing: KF5IconThemes_DIR)
-- Could NOT find KF5IconThemes: found neither KF5IconThemesConfig.cmake nor kf5iconthemes-config.cmake 
-- Could NOT find KF5ItemModels (missing: KF5ItemModels_DIR)
-- Could NOT find KF5ItemModels: found neither KF5ItemModelsConfig.cmake nor kf5itemmodels-config.cmake 
-- Could NOT find KF5I18n (missing: KF5I18n_DIR)
-- Could NOT find KF5I18n: found neither KF5I18nConfig.cmake nor kf5i18n-config.cmake 
-- Could NOT find KF5JobWidgets (missing: KF5JobWidgets_DIR)
-- Could NOT find KF5JobWidgets: found neither KF5JobWidgetsConfig.cmake nor kf5jobwidgets-config.cmake 
-- Could NOT find KF5KIO (missing: KF5KIO_DIR)
-- Could NOT find KF5KIO: found neither KF5KIOConfig.cmake nor kf5kio-config.cmake 
-- Could NOT find KF5Solid (missing: KF5Solid_DIR)
-- Could NOT find KF5Solid: found neither KF5SolidConfig.cmake nor kf5solid-config.cmake 
-- Could NOT find KF5Wallet (missing: KF5Wallet_DIR)
-- Could NOT find KF5Wallet: found neither KF5WalletConfig.cmake nor kf5wallet-config.cmake 
-- Could NOT find KF5WidgetsAddons (missing: KF5WidgetsAddons_DIR)
-- Could NOT find KF5WidgetsAddons: found neither KF5WidgetsAddonsConfig.cmake nor kf5widgetsaddons-config.cmake 
-- Could NOT find KF5WindowSystem (missing: KF5WindowSystem_DIR)
-- Could NOT find KF5WindowSystem: found neither KF5WindowSystemConfig.cmake nor kf5windowsystem-config.cmake 
-- Could NOT find KF5XmlGui (missing: KF5XmlGui_DIR)
-- Could NOT find KF5XmlGui: found neither KF5XmlGuiConfig.cmake nor kf5xmlgui-config.cmake 
CMake Error at /usr/share/cmake-3.10/Modules/FindPackageHandleStandardArgs.cmake:137 (message):
  Could NOT find KF5 (missing: Archive Codecs Config ConfigWidgets CoreAddons
  Crash DocTools GuiAddons IconThemes ItemModels I18n JobWidgets KIO Solid
  Wallet WidgetsAddons WindowSystem XmlGui)
Call Stack (most recent call first):
  /usr/share/cmake-3.10/Modules/FindPackageHandleStandardArgs.cmake:378 (_FPHSA_FAILURE_MESSAGE)
  /usr/share/ECM/find-modules/FindKF5.cmake:110 (find_package_handle_standard_args)
  CMakeLists.txt:59 (find_package)


-- Configuring incomplete, errors occurred!

```

This is after having installed [libpoppler-qt5-dev libtaglib-ocaml-dev libexempi-dev libyaz-dev libkf5kdelibs4support5-bin extra-cmake-modules] and following the instructions shown here: [https://techbase.kde.org/Projects/Tellico/Compiling](https://techbase.kde.org/Projects/Tellico/Compiling)

---

### Post by wildmanne39 on 2019-06-29
The version you are trying to install is 3.10 and it is from 9 April 2017, also that is the date the page was last updated, I am pretty sure that it is to old to compile on 18.04.

---

### Post by CatKiller on 2019-06-29
The 3.1.2 version in the 18.04 repositories is significantly newer (March 2018) than the 3.0 version (February 2017) you're getting from the page that you linked. According to the changelog, the old version you're trying to build from source doesn't build with CMake > 3.9 (you're using CMake 3.10) - that bug was fixed in tellico 3.1.

The latest version is 3.2, from May 2019. You can get that from [here](http://tellico-project.org/), although they say you should use the one that's in the Ubuntu repositories, too.

As far as I can tell from your output, you're missing a huge bunch of KDE Framework 5 stuff. You'd probably need the -dev versions of those packages to be able to build against them.

---

### Post by rebeltaz on 2019-06-30
I should have been more clear... I did get the source code from ([http://tellico-project.org/download](http://tellico-project.org/download)) - the 3.2 verson. I was just following the build instructions for the 3.0 version because I couldn't find anything anywhere else on how to build the 3.2 version. 

I do have the 3.1.2 version from the repositories, but most of the search functions are broken now (due to API changes in the sources, I suppose) so it's no where near as useful as it was when it was first installed. Hence why I need to get the newer version.

---

### Post by CatKiller on 2019-06-30
Well, I've not compiled much at all, and not that application you're interested in, but the output you posted showed that it's looking for a bunch of KDE Frameworks 5 stuff that you don't have, and strlwr and strupr; I'm not sure what those are, but I'd speculate that they're something to do with string manipulation. You could find the -dev packages that provide those, and then try again. There may well then be *different* things that it needs, that you'll need to install. And you keep doing that till it works.

It's *not* having to do all that which makes package managers awesome.

You might be able to find a PPA with it in, but I couldn't find one when I had a quick look the other night.

---

### Post by rebeltaz on 2019-06-30
> **CatKiller said:**
> It's *not* having to do all that which makes package managers awesome.

You might be able to find a PPA with it in, but I couldn't find one when I had a quick look the other night.

Yeah, I looked for a PPA, too.. but I couldn't find one, either :(

And yeah... package managers are wonderful!!!!

---

### Post by rebeltaz on 2019-07-08
I just wanted to thank everyone. I finally managed to get it built. I took a LOT of libraries, but I finally got it! Thanks again.

---

