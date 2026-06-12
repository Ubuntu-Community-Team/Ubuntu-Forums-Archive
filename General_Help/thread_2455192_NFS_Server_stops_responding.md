---
title: "NFS Server stops responding"
date: 2020-12-14
forum: General Help
---

### Post by unixcommando on 2020-12-14
Greetings

    I'm running Ubuntu 20.10 on a Raspberry Pi 4, kernel 5.8.0-1008-raspi 64 bit.  Ubuntu is up to date.

    I'm using this server as a NAS server for NFS and CIFS.  I have a JBOD with 4 10T drives in a ZRAID configuration.  I'm currently sharing 2 file systems via NFS.  Twice now my NFS server has stopped responding.  What isn't clear is if NFS has stopped working or has stopped sharing the file systems.  Last night was the second time and I logged into the Pi 4 and it seemed that the ZFS file systems were responding properly, I could navigate around them and open and read from files within them.  I restarted nfs-server in the hopes that it would fix things but it did not.  Since it was getting late and I needed to get to sleep I rebooted both the nfs-server and the nfs-client which was having problems due to non-responsive NFS share.  When the client came back online I edited FSTAB to mount the NFS share soft so it wouldn't hose the client in the future.  Log files on the client showed a large number of "NFS server not responding" messages.  So far I've found nothing on the NFS server that is cluing me in.  I don't know if it will help, but I added the file systems to /etc/exports, this shouldn't be necessary for ZFS, but right now the only thing I can think of is somehow the ZFS exports stopped working.

    I have a friend with nearly the same setup but he's not having the issue, the primary difference between his setup and mine is mine is up to date on Ubuntu and his hasn't been updated in nearly a year.

Is there anything else I can look at?  I was really excited to use ZFS as I'm an old Solaris guy and like ZFS a great deal.  I'd hate to have to redo my NAS to something else, but will if ZFS is the problem here, reliable NAS is more important.

Thanks
-Bob

---

### Post by TheFu on 2020-12-15
Running ZFS on a r-pi? 
It isn't clear which nfs-server is being used - the one built-into ZFS or the stand alone one.  If the later, the /etc/exports is NOT optional.

Please post config files for the server and the client (wrapped in code-tags) [https://ubuntuforums.org/misc.php?do=bbcode#code](https://ubuntuforums.org/misc.php?do=bbcode#code)
How can anyone blindly guess at issues without any facts?  Also, if the networking is flaky, NFS is going to to have issues. Please don't tell me the server is using WiFi for connectivity.

---

### Post by unixcommando on 2020-12-15
There is no NFS server with ZFS, however ZFS handles share permissions for both NFS and CIFS.  After rebooting the machine the NFS shares are available to the clients for a couple of days and then simply stop responding.  

Pool attributes listed below.  /etc/exports is not populated.

root@storage:~# zfs get all pool1/tv
NAME      PROPERTY              VALUE                  SOURCE
pool1/tv  type                  filesystem             -
pool1/tv  creation              Mon Nov 30 17:57 2020  -
pool1/tv  used                  1.04T                  -
pool1/tv  available             21.8T                  -
pool1/tv  referenced            1.04T                  -
pool1/tv  compressratio         1.00x                  -
pool1/tv  mounted               yes                    -
pool1/tv  quota                 none                   default
pool1/tv  reservation           none                   default
pool1/tv  recordsize            128K                   default
pool1/tv  mountpoint            /tv                    local
pool1/tv  sharenfs              on                     local
pool1/tv  checksum              on                     default
pool1/tv  compression           off                    default
pool1/tv  atime                 on                     default
pool1/tv  devices               on                     default
pool1/tv  exec                  on                     default
pool1/tv  setuid                on                     default
pool1/tv  readonly              off                    default
pool1/tv  zoned                 off                    default
pool1/tv  snapdir               hidden                 default
pool1/tv  aclinherit            restricted             default
pool1/tv  createtxg             77                     -
pool1/tv  canmount              on                     default
pool1/tv  xattr                 on                     default
pool1/tv  copies                1                      default
pool1/tv  version               5                      -
pool1/tv  utf8only              off                    -
pool1/tv  normalization         none                   -
pool1/tv  casesensitivity       sensitive              -
pool1/tv  vscan                 off                    default
pool1/tv  nbmand                off                    default
pool1/tv  sharesmb              off                    default
pool1/tv  refquota              none                   default
pool1/tv  refreservation        none                   default
pool1/tv  guid                  9373054160225552910    -
pool1/tv  primarycache          all                    default
pool1/tv  secondarycache        all                    default
pool1/tv  usedbysnapshots       0B                     -
pool1/tv  usedbydataset         1.04T                  -
pool1/tv  usedbychildren        0B                     -
pool1/tv  usedbyrefreservation  0B                     -
pool1/tv  logbias               latency                default
pool1/tv  objsetid              144                    -
pool1/tv  dedup                 off                    default
pool1/tv  mlslabel              none                   default
pool1/tv  sync                  standard               default
pool1/tv  dnodesize             legacy                 default
pool1/tv  refcompressratio      1.00x                  -
pool1/tv  written               1.04T                  -
pool1/tv  logicalused           1.04T                  -
pool1/tv  logicalreferenced     1.04T                  -
pool1/tv  volmode               default                default
pool1/tv  filesystem_limit      none                   default
pool1/tv  snapshot_limit        none                   default
pool1/tv  filesystem_count      none                   default
pool1/tv  snapshot_count        none                   default
pool1/tv  snapdev               hidden                 default
pool1/tv  acltype               off                    default
pool1/tv  context               none                   default
pool1/tv  fscontext             none                   default
pool1/tv  defcontext            none                   default
pool1/tv  rootcontext           none                   default
pool1/tv  relatime              off                    default
pool1/tv  redundant_metadata    all                    default
pool1/tv  overlay               off                    default
pool1/tv  encryption            off                    default
pool1/tv  keylocation           none                   default
pool1/tv  keyformat             none                   default
pool1/tv  pbkdf2iters           0                      default
pool1/tv  special_small_blocks  0                      default

Regards
-Bob

---

