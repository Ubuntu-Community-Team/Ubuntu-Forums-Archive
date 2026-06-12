---
title: "mount and squashfs"
date: 2015-08-21
forum: General Help
---

### Post by roland-logikalsolutions on 2015-08-21
This should be easy. I committed the cardinal sin of programming, stealing code I did not write. If you scroll way down into the comments on this page:

[https://help.ubuntu.com/community/LiveCDCustomization](https://help.ubuntu.com/community/LiveCDCustomization)

You will see response where someone posted code to customize kubuntu. The portion which is interesting is here:

```

function mnt {
    local margs="$1" ; shift
    local mp="$WDIR/$1"
    for D in "$@" ; do
        mkdir -v -p "$WDIR/$D"
    done
    mount -v $margs "$mp"
    addExit "umount -v $mp"
}

# mount the CD image
mnt "-t auto $CD -o loop,ro" cd

# mount compressed filesystem
mnt "-t squashfs $WDIR/cd/casper/filesystem.squashfs -o ro,loop" sq

# create joined writable filesystem for the new CD
mnt "-t aufs -o br:$WDIR/cd-w=rw:$WDIR/cd=ro none" cd-u cd-w

# create joined writable filesystem for the new compressed squashfs filesystem
mnt "-t aufs -o br:$WDIR/sq-w=rw:$WDIR/sq=ro none" sq-u sq-w

echo ">>> Updating CD content"

(
    cd sq-u

    # DO YOUR CUSTOMIZATION STUFF HERE, CHROOT, MODIFY FILES, ETC.
    # ...
    # ...

)

echo ">>> Compressing filesystem"
mksquashfs $WDIR/sq-u/ $WDIR/cd-u/casper/filesystem.squashfs -noappend

```


Most likely I just don't know enough about mount. I can copy/edit/nuke files directly using cd-u and they all make it into the new ISO. When I try to chroot using sq-u to apply language packs, I see all of the files in the sq-w directory after the ISO is build, but, none of them make it into the ISO. I should not say "none" because I have not checked just how many *-ru.* files exist in a basic Ubuntu 15.04 installation. I just know I see a tiny number compared to the big pile in sq-w.

Just in case this is something stupid I did, highly possible, but I think this is due more to my stupidity with mount. Here is a subset of the external shell script run within chroot because chroot only executes the first command within the root when running from within a script.

```

mount -t proc none /proc
mount -t sysfs none /sys
mount -t devpts none /dev/pts

export HOME=/root
export LC_ALL=C

dbus-uuidgen > /var/lib/dbus/machine-id

dpkg-divert --local --rename --add /sbin/initctl
ln -s /bin/true /sbin/initctl

echo ">>>>> Now applying updates"

# Update package info
#
echo ">>>>> update package list"
apt-get update

echo ">>>>> installing language packs"
apt-get -y install `check-language-support -l af`
apt-get -y install `check-language-support -l am`
apt-get -y install `check-language-support -l an`

apt-get clean
rm -rf /tmp/* ~/.bash_history

rm /var/lib/dbus/machine-id

rm /sbin/initctl
dpkg-divert --rename --remove /sbin/initctl

umount /dev/pts
umount /sys
umount /proc || umount -lf /proc

exit


```

Is the real problem this line?
mksquashfs $WDIR/sq-u/ $WDIR/cd-u/casper/filesystem.squashfs -noappend

I'm going to do some more experimentation, but ...

How does one get the writes written to the writeable mount into the actual squash?

Thanks,

---

### Post by roland-logikalsolutions on 2015-08-21
Well,

It took all day, but the answer is this:

chroot is a busted pathetic puddle of (^)(&*)(*&)(*&)(*

I feel better now.

The long answer, one which took a couple of days to find is this. 

If you never ever under any circumstances issue a chroot into sq-u after having mounted sq-u sq-w then you need do nothing. All will work as it should.

Once you issue a chroot into sq-u, you can frustratingly issue directory commands showing all of your files there just as you expect after getting out of chroot. The entire thing will look perfect, but it will be ignored. chroot manages to discombobulate the connection(s) from sq to sq-u to sq-w. In this case, and seemingly only this case, you need to do the following just in front of md5sum creation before mkisofs.

echo ">>> Compressing filesystem"
mksquashfs $WDIR/sq-u/ $WDIR/cd-u/casper/filesystem.squashfs -noappend


I did not feel like spending any more time digging to see if there was some method of issuing chroot AND having it preserve the connection to sq-w so everything would automatically roll up. In "theory" that "should" be possible. It is just too late on Friday for me to start digging.

---

