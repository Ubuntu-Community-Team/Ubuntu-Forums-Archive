---
title: "Help installing Catalyst 13.1 on Ubuntu 12.10"
date: 2013-02-01
forum: General Help
---

### Post by ThePhysician on 2013-02-01
I am trying to install the driver found here:
[http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.42&lang=English](http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.42&lang=English)

It is the correct driver for my card, and I'm trying to follow these directions:
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI#Manually_installing_Catalyst_12.6](https://help.ubuntu.com/community/BinaryDriverHowto/ATI#Manually_installing_Catalyst_12.6)

I'm running Quantal Quetzal, and can not seem to get these to install.

It says it should automatically install some dependencies, well it doesn't.

I got the required packages installed from step 2, but step 3 keeps giving me an error. Here is my terminal output:

```
sudo sh amd-driver-installer-catalyst-13.1-linux-x86.x86_64.run --buildpkg Ubuntu/quantal
Created directory fglrx-install.1aOMZc
Verifying archive integrity... All good.
Uncompressing AMD Catalyst(TM) Proprietary Driver-9.012.....................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................
=====================================================================
 AMD Catalyst(TM) Proprietary Driver Installer/Packager 
=====================================================================
Generating package: Ubuntu/quantal
Resolving build dependencies...
apt 0.9.7.5ubuntu5.1 for i386 compiled on Dec 12 2012 13:47:56
Usage: apt-get [options] command
       apt-get [options] install|remove pkg1 [pkg2 ...]
       apt-get [options] source pkg1 [pkg2 ...]

apt-get is a simple command line interface for downloading and
installing packages. The most frequently used commands are update
and install.

Commands:
   update - Retrieve new lists of packages
   upgrade - Perform an upgrade
   install - Install new packages (pkg is libc6 not libc6.deb)
   remove - Remove packages
   autoremove - Remove automatically all unused packages
   purge - Remove packages and config files
   source - Download source archives
   build-dep - Configure build-dependencies for source packages
   dist-upgrade - Distribution upgrade, see apt-get(8)
   dselect-upgrade - Follow dselect selections
   clean - Erase downloaded archive files
   autoclean - Erase old downloaded archive files
   check - Verify that there are no broken dependencies
   changelog - Download and display the changelog for the given package
   download - Download the binary package into the current directory

Options:
  -h  This help text.
  -q  Loggable output - no progress indicator
  -qq No output except for errors
  -d  Download only - do NOT install or unpack archives
  -s  No-act. Perform ordering simulation
  -y  Assume Yes to all queries and do not prompt
  -f  Attempt to correct a system with broken dependencies in place
  -m  Attempt to continue if archives are unlocatable
  -u  Show a list of upgraded packages as well
  -b  Build the source package after fetching it
  -V  Show verbose version numbers
  -c=? Read this configuration file
  -o=? Set an arbitrary configuration option, eg -o dir::cache=/tmp
See the apt-get(8), sources.list(5) and apt.conf(5) manual
pages for more information and options.
                       This APT has Super Cow Powers.
Unable to resolve  build-essential.  Please manually install and try again.
Package build failed!
Package build utility output:
./packages/Ubuntu/ati-packager.sh: 294: ./packages/Ubuntu/ati-packager.sh: debclean: not found
dpkg-buildpackage: source package fglrx-installer
dpkg-buildpackage: source version 2:9.012-0ubuntu1
dpkg-buildpackage: source changed by AMD: Advanced Micro Devices. <http://ati.amd.com/support/driver.html>
 dpkg-source --before-build fglrx.35aII6
dpkg-buildpackage: host architecture i386
 debian/rules build
#Create important strings
for i in 10fglrx \
			 dkms.conf \
			 fglrx.install \
			 fglrx-dev.install \
			 fglrx-dev.links \
			 fglrx-amdcccle.install \
			 fglrx.grub-gfxpayload \
			 fglrx.dirs \
			 fglrx.links \
			 fglrx.postinst \
			 fglrx.postrm \
			 fglrx.preinst \
			 fglrx.prerm \
			 overrides/fglrx; do \
		sed -e "s|#PKGXMODDIR#|usr/lib/fglrx/xorg/modules|g" \
			-e "s|#LIBDIR#|usr/lib|g" \
			-e "s|#LIBDIR32#|usr/lib32|g" \
			-e "s|#BINDIR#|usr/bin|g" \
			-e "s|#SYSCONFDIR#|etc|g" \
			-e "s|#MANDIR#|usr/share/man/man1|g" \
			-e "s|#LDSOCONF#|usr/lib/fglrx/ld.so.conf|g" \
			-e "s|#ALTLDSOCONF#|usr/lib/fglrx/alt_ld.so.conf|g" \
			-e "s|#ALTPRIORITY#|1000|g" \
			-e "s|#PXALTPRIORITY#|900|g" \
			-e "s|#AUTOSTARTDIR#|etc/xdg/autostart|g" \
			-e "s|#DATADIR#|usr/share|g" \
			-e "s|#PKGDESKDIR#|usr/share/fglrx|g" \
			-e "s|#PKGDATADIR#|usr/share/fglrx|g" \
			-e "s|#PKGCONFIGDIR#|usr/lib/fglrx|g" \
			-e "s|#PKGBINDIR#|usr/lib/fglrx/bin|g" \
			-e "s|#PKGLIBDIR#|usr/lib/fglrx|g" \
			-e "s|#PKGLIBDIR32#|usr/lib32/fglrx|g" \
			-e "s|#PKGDRIVERSDIR#|usr/lib/fglrx/xorg|g" \
			-e "s|#XORGEXTRA#|usr/lib/i386-linux-gnu/xorg/extra-modules|g" \
			-e "s|#PKGEXTENSIONDIR#|usr/lib/fglrx/xorg|g" \
			-e "s|#XORGEXTENSIONSDIR#|usr/lib/xorg/modules/extensions|g" \
			-e "s|#DRIVERNAME#|fglrx|g" \
			-e "s|#DRIVERDEVNAME#|fglrx-dev|g" \
			-e "s|#DRIVERSRCNAME#||g" \
			-e "s|#INCLUDEDIR#|usr/include|g" \
			-e "s|#PKGLIBCONFDIR#|lib/fglrx|g" \
			-e "s|#GRUBBLKLISTDIR#|usr/share/grub-gfxpayload-lists/blacklist|g" \
			-e "s|#PKGXMODDIR#|usr/lib/fglrx/xorg/modules|g" \
			-e "s|#PXDIR#|usr/lib/pxpress|g" \
			-e "s|#PXDIR32#|usr/lib32/pxpress|g" \
			-e "s|#PXXMODDIR#|usr/lib/pxpress/xorg/modules|g" \
			-e "s|#PXDIRNAME#|pxpress|g" \
			-e "s|#PXLIBDIR#|usr/lib/pxpress/lib|g" \
			-e "s|#PXLIBDIR32#|usr/lib32/pxpress/lib|g" \
			-e "s|#PXLDSOCONF#|usr/lib/pxpress/ld.so.conf|g" \
			-e "s|#ALTPXLDSOCONF#|usr/lib/pxpress/alt_ld.so.conf|g" \
			-e "s|#CVERSION#|9.012|g" \
			-e "s|#SRCXARCH#|xpic|g" \
			-e "s|#SRCARCH#|x86|g" \
			-e "s|#SRCOTHERARCH#|x86_64|g" \
			-e "s|#SRCLIBDIR#|lib|g" \
			-e "s|#DEB_HOST_MULTIARCH#|i386-linux-gnu|g" \
			-e "s|#OTHER_ARCH#|x86_64-linux-gnu|g" \
			debian/$i.in > debian/$i;      \
	done
# remove exec bit on everything
find arch \
		etc \
		lib \
		module \
		usr \
		xpic     -type f | xargs chmod -x
find: `module': No such file or directory
# set executable on user apps
find arch/x86/usr/sbin \
		arch/x86/usr/X11R6/bin \
		usr/sbin/ -type f | xargs chmod a+x
# set exec bit on scripts
find lib etc debian -name "*.sh" -type f | xargs chmod +x
# set the permissions on the pxpress scripts
chmod 744 debian/pxpress/switch*
dh build
   dh_testdir
   dh_auto_configure
   dh_auto_build
   dh_auto_test
dh build
 debian/rules binary
# refresh copyright file
cat debian/copyright_stub_0 > debian/copyright
cat usr/share/doc/fglrx/LICENSE.TXT >> debian/copyright
cat debian/copyright_stub_1 >> debian/copyright
#Steps that we can't easily represent in debhelper files or .in files yet
# Remove any libraries that may be caught by shell expansion
find . -name libGLE* | xargs rm -f
find . -name libEGL* | xargs rm -f
dh_installdirs -pfglrx
# Install the QT libraries
dh_install -pfglrx "arch/x86_64/usr/share/ati/lib" "usr/share/ati"
cp: cannot stat `debian/tmp/arch/x86_64/usr/share/ati/lib': No such file or directory
dh_install: cp -a debian/tmp/arch/x86_64/usr/share/ati/lib debian/fglrx/usr/share/ati/ returned exit code 1
make: *** [binary-arch] Error 2
dpkg-buildpackage: error: debian/rules binary gave error exit status 2
./packages/Ubuntu/ati-packager.sh: 294: ./packages/Ubuntu/ati-packager.sh: debclean: not found
dpkg-buildpackage: source package fglrx-installer
dpkg-buildpackage: source version 2:9.012-0ubuntu1
dpkg-buildpackage: source changed by AMD: Advanced Micro Devices. <http://ati.amd.com/support/driver.html>
 dpkg-source --before-build fglrx.tk9wdR
dpkg-buildpackage: host architecture i386
 debian/rules build
#Create important strings
for i in 10fglrx \
			 dkms.conf \
			 fglrx.install \
			 fglrx-dev.install \
			 fglrx-dev.links \
			 fglrx-amdcccle.install \
			 fglrx.grub-gfxpayload \
			 fglrx.dirs \
			 fglrx.links \
			 fglrx.postinst \
			 fglrx.postrm \
			 fglrx.preinst \
			 fglrx.prerm \
			 overrides/fglrx; do \
		sed -e "s|#PKGXMODDIR#|usr/lib/fglrx/xorg/modules|g" \
			-e "s|#LIBDIR#|usr/lib|g" \
			-e "s|#LIBDIR32#|usr/lib32|g" \
			-e "s|#BINDIR#|usr/bin|g" \
			-e "s|#SYSCONFDIR#|etc|g" \
			-e "s|#MANDIR#|usr/share/man/man1|g" \
			-e "s|#LDSOCONF#|usr/lib/fglrx/ld.so.conf|g" \
			-e "s|#ALTLDSOCONF#|usr/lib/fglrx/alt_ld.so.conf|g" \
			-e "s|#ALTPRIORITY#|1000|g" \
			-e "s|#PXALTPRIORITY#|900|g" \
			-e "s|#AUTOSTARTDIR#|etc/xdg/autostart|g" \
			-e "s|#DATADIR#|usr/share|g" \
			-e "s|#PKGDESKDIR#|usr/share/fglrx|g" \
			-e "s|#PKGDATADIR#|usr/share/fglrx|g" \
			-e "s|#PKGCONFIGDIR#|usr/lib/fglrx|g" \
			-e "s|#PKGBINDIR#|usr/lib/fglrx/bin|g" \
			-e "s|#PKGLIBDIR#|usr/lib/fglrx|g" \
			-e "s|#PKGLIBDIR32#|usr/lib32/fglrx|g" \
			-e "s|#PKGDRIVERSDIR#|usr/lib/fglrx/xorg|g" \
			-e "s|#XORGEXTRA#|usr/lib/i386-linux-gnu/xorg/extra-modules|g" \
			-e "s|#PKGEXTENSIONDIR#|usr/lib/fglrx/xorg|g" \
			-e "s|#XORGEXTENSIONSDIR#|usr/lib/xorg/modules/extensions|g" \
			-e "s|#DRIVERNAME#|fglrx|g" \
			-e "s|#DRIVERDEVNAME#|fglrx-dev|g" \
			-e "s|#DRIVERSRCNAME#||g" \
			-e "s|#INCLUDEDIR#|usr/include|g" \
			-e "s|#PKGLIBCONFDIR#|lib/fglrx|g" \
			-e "s|#GRUBBLKLISTDIR#|usr/share/grub-gfxpayload-lists/blacklist|g" \
			-e "s|#PKGXMODDIR#|usr/lib/fglrx/xorg/modules|g" \
			-e "s|#PXDIR#|usr/lib/pxpress|g" \
			-e "s|#PXDIR32#|usr/lib32/pxpress|g" \
			-e "s|#PXXMODDIR#|usr/lib/pxpress/xorg/modules|g" \
			-e "s|#PXDIRNAME#|pxpress|g" \
			-e "s|#PXLIBDIR#|usr/lib/pxpress/lib|g" \
			-e "s|#PXLIBDIR32#|usr/lib32/pxpress/lib|g" \
			-e "s|#PXLDSOCONF#|usr/lib/pxpress/ld.so.conf|g" \
			-e "s|#ALTPXLDSOCONF#|usr/lib/pxpress/alt_ld.so.conf|g" \
			-e "s|#CVERSION#|9.012|g" \
			-e "s|#SRCXARCH#|xpic|g" \
			-e "s|#SRCARCH#|x86|g" \
			-e "s|#SRCOTHERARCH#|x86_64|g" \
			-e "s|#SRCLIBDIR#|lib|g" \
			-e "s|#DEB_HOST_MULTIARCH#|i386-linux-gnu|g" \
			-e "s|#OTHER_ARCH#|x86_64-linux-gnu|g" \
			debian/$i.in > debian/$i;      \
	done
# remove exec bit on everything
find arch \
		etc \
		lib \
		module \
		usr \
		xpic     -type f | xargs chmod -x
find: `module': No such file or directory
# set executable on user apps
find arch/x86/usr/sbin \
		arch/x86/usr/X11R6/bin \
		usr/sbin/ -type f | xargs chmod a+x
# set exec bit on scripts
find lib etc debian -name "*.sh" -type f | xargs chmod +x
# set the permissions on the pxpress scripts
chmod 744 debian/pxpress/switch*
dh build
   dh_testdir
   dh_auto_configure
   dh_auto_build
   dh_auto_test
dh build
 debian/rules binary
# refresh copyright file
cat debian/copyright_stub_0 > debian/copyright
cat usr/share/doc/fglrx/LICENSE.TXT >> debian/copyright
cat debian/copyright_stub_1 >> debian/copyright
#Steps that we can't easily represent in debhelper files or .in files yet
# Remove any libraries that may be caught by shell expansion
find . -name libGLE* | xargs rm -f
find . -name libEGL* | xargs rm -f
dh_installdirs -pfglrx
# Install the QT libraries
dh_install -pfglrx "arch/x86_64/usr/share/ati/lib" "usr/share/ati"
cp: cannot stat `debian/tmp/arch/x86_64/usr/share/ati/lib': No such file or directory
dh_install: cp -a debian/tmp/arch/x86_64/usr/share/ati/lib debian/fglrx/usr/share/ati/ returned exit code 1
make: *** [binary-arch] Error 2
dpkg-buildpackage: error: debian/rules binary gave error exit status 2
./packages/Ubuntu/ati-packager.sh: 294: ./packages/Ubuntu/ati-packager.sh: debclean: not found
dpkg-buildpackage: source package fglrx-installer
dpkg-buildpackage: source version 2:9.012-0ubuntu1
dpkg-buildpackage: source changed by AMD: Advanced Micro Devices. <http://ati.amd.com/support/driver.html>
 dpkg-source --before-build fglrx.b4mFuS
dpkg-buildpackage: host architecture i386
 debian/rules build
#Create important strings
for i in 10fglrx \
			 dkms.conf \
			 fglrx.install \
			 fglrx-dev.install \
			 fglrx-dev.links \
			 fglrx-amdcccle.install \
			 fglrx.grub-gfxpayload \
			 fglrx.dirs \
			 fglrx.links \
			 fglrx.postinst \
			 fglrx.postrm \
			 fglrx.preinst \
			 fglrx.prerm \
			 overrides/fglrx; do \
		sed -e "s|#PKGXMODDIR#|usr/lib/fglrx/xorg/modules|g" \
			-e "s|#LIBDIR#|usr/lib|g" \
			-e "s|#LIBDIR32#|usr/lib32|g" \
			-e "s|#BINDIR#|usr/bin|g" \
			-e "s|#SYSCONFDIR#|etc|g" \
			-e "s|#MANDIR#|usr/share/man/man1|g" \
			-e "s|#LDSOCONF#|usr/lib/fglrx/ld.so.conf|g" \
			-e "s|#ALTLDSOCONF#|usr/lib/fglrx/alt_ld.so.conf|g" \
			-e "s|#ALTPRIORITY#|1000|g" \
			-e "s|#PXALTPRIORITY#|900|g" \
			-e "s|#AUTOSTARTDIR#|etc/xdg/autostart|g" \
			-e "s|#DATADIR#|usr/share|g" \
			-e "s|#PKGDESKDIR#|usr/share/fglrx|g" \
			-e "s|#PKGDATADIR#|usr/share/fglrx|g" \
			-e "s|#PKGCONFIGDIR#|usr/lib/fglrx|g" \
			-e "s|#PKGBINDIR#|usr/lib/fglrx/bin|g" \
			-e "s|#PKGLIBDIR#|usr/lib/fglrx|g" \
			-e "s|#PKGLIBDIR32#|usr/lib32/fglrx|g" \
			-e "s|#PKGDRIVERSDIR#|usr/lib/fglrx/xorg|g" \
			-e "s|#XORGEXTRA#|usr/lib/i386-linux-gnu/xorg/extra-modules|g" \
			-e "s|#PKGEXTENSIONDIR#|usr/lib/fglrx/xorg|g" \
			-e "s|#XORGEXTENSIONSDIR#|usr/lib/xorg/modules/extensions|g" \
			-e "s|#DRIVERNAME#|fglrx|g" \
			-e "s|#DRIVERDEVNAME#|fglrx-dev|g" \
			-e "s|#DRIVERSRCNAME#||g" \
			-e "s|#INCLUDEDIR#|usr/include|g" \
			-e "s|#PKGLIBCONFDIR#|lib/fglrx|g" \
			-e "s|#GRUBBLKLISTDIR#|usr/share/grub-gfxpayload-lists/blacklist|g" \
			-e "s|#PKGXMODDIR#|usr/lib/fglrx/xorg/modules|g" \
			-e "s|#PXDIR#|usr/lib/pxpress|g" \
			-e "s|#PXDIR32#|usr/lib32/pxpress|g" \
			-e "s|#PXXMODDIR#|usr/lib/pxpress/xorg/modules|g" \
			-e "s|#PXDIRNAME#|pxpress|g" \
			-e "s|#PXLIBDIR#|usr/lib/pxpress/lib|g" \
			-e "s|#PXLIBDIR32#|usr/lib32/pxpress/lib|g" \
			-e "s|#PXLDSOCONF#|usr/lib/pxpress/ld.so.conf|g" \
			-e "s|#ALTPXLDSOCONF#|usr/lib/pxpress/alt_ld.so.conf|g" \
			-e "s|#CVERSION#|9.012|g" \
			-e "s|#SRCXARCH#|xpic|g" \
			-e "s|#SRCARCH#|x86|g" \
			-e "s|#SRCOTHERARCH#|x86_64|g" \
			-e "s|#SRCLIBDIR#|lib|g" \
			-e "s|#DEB_HOST_MULTIARCH#|i386-linux-gnu|g" \
			-e "s|#OTHER_ARCH#|x86_64-linux-gnu|g" \
			debian/$i.in > debian/$i;      \
	done
# remove exec bit on everything
find arch \
		etc \
		lib \
		module \
		usr \
		xpic     -type f | xargs chmod -x
find: `module': No such file or directory
# set executable on user apps
find arch/x86/usr/sbin \
		arch/x86/usr/X11R6/bin \
		usr/sbin/ -type f | xargs chmod a+x
# set exec bit on scripts
find lib etc debian -name "*.sh" -type f | xargs chmod +x
# set the permissions on the pxpress scripts
chmod 744 debian/pxpress/switch*
dh build
   dh_testdir
   dh_auto_configure
   dh_auto_build
   dh_auto_test
dh build
 debian/rules binary
# refresh copyright file
cat debian/copyright_stub_0 > debian/copyright
cat usr/share/doc/fglrx/LICENSE.TXT >> debian/copyright
cat debian/copyright_stub_1 >> debian/copyright
#Steps that we can't easily represent in debhelper files or .in files yet
# Remove any libraries that may be caught by shell expansion
find . -name libGLE* | xargs rm -f
find . -name libEGL* | xargs rm -f
dh_installdirs -pfglrx
# Install the QT libraries
dh_install -pfglrx "arch/x86_64/usr/share/ati/lib" "usr/share/ati"
cp: cannot stat `debian/tmp/arch/x86_64/usr/share/ati/lib': No such file or directory
dh_install: cp -a debian/tmp/arch/x86_64/usr/share/ati/lib debian/fglrx/usr/share/ati/ returned exit code 1
make: *** [binary-arch] Error 2
dpkg-buildpackage: error: debian/rules binary gave error exit status 2
Removing temporary directory: fglrx-install.1aOMZc

```

Really hoping that with an HD 5780 I can at least get Team Fortress 2 running. =(

I just can't figure out how to get the dependant packages that the guide says should be automagically grabbed and installed. Rahh.

---

### Post by windscape on 2013-02-01
Hi,

I think the directions [here]("http://wiki.cchtml.com/index.php/Ubuntu_Quantal_Installation_Guide") will help.

---

