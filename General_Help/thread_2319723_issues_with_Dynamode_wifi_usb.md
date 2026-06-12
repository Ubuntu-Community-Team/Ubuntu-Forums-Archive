---
title: "issues with Dynamode wifi usb"
date: 2016-04-06
forum: General Help
---

### Post by enkill3 on 2016-04-06
i had it working beautifully on a previous install, but cannot, for love nor money get it working on the new one,

LSUSB GIVES 

Bus 001 Device 004: ID 0bda:818b Realtek Semiconductor Corp.

ive tried installing the driver included with the CD, and it seems to be working fine, but then i get an error, Please help


```
##################################################
Realtek Wi-Fi driver Auto installation script
Novembor, 21 2011 v1.1.0
##################################################
Decompress the driver source tar ball:
    
rtl8192EU_linux_v4.2.2_7585.20130524
Authentication requested [root] for make clean:
cd hal/OUTSRC/ ; rm -fr */*.mod.c */*.mod */*.o */.*.cmd */*.ko
cd hal/OUTSRC/ ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko 
cd hal/led ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko
cd hal ; rm -fr */*/*.mod.c */*/*.mod */*/*.o */*/.*.cmd */*/*.ko
cd hal ; rm -fr */*.mod.c */*.mod */*.o */.*.cmd */*.ko
cd hal ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko
cd core/efuse ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko
cd core ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko
cd os_dep/linux ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko
cd os_dep ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko
rm -fr Module.symvers ; rm -fr Module.markers ; rm -fr modules.order
rm -fr *.mod.c *.mod *.o .*.cmd *.ko *~
rm -fr .tmp_versions
Authentication requested [root] for make driver:
make ARCH=x86_64 CROSS_COMPILE= -C /lib/modules/4.2.0-35-generic/build M=/home/ryletti/Downloads/install_folder/driver/rtl8192EU_linux_v4.2.2_7585.20130524  modules
make[1]: Entering directory `/usr/src/linux-headers-4.2.0-35-generic'
  CC [M]  /home/ryletti/Downloads/install_folder/driver/rtl8192EU_linux_v4.2.2_7585.20130524/core/rtw_cmd.o
  CC [M]  /home/ryletti/Downloads/install_folder/driver/rtl8192EU_linux_v4.2.2_7585.20130524/core/rtw_security.o
  CC [M]  /home/ryletti/Downloads/install_folder/driver/rtl8192EU_linux_v4.2.2_7585.20130524/core/rtw_debug.o
  CC [M]  /home/ryletti/Downloads/install_folder/driver/rtl8192EU_linux_v4.2.2_7585.20130524/core/rtw_io.o
  CC [M]  /home/ryletti/Downloads/install_folder/driver/rtl8192EU_linux_v4.2.2_7585.20130524/core/rtw_ioctl_query.o
  CC [M]  /home/ryletti/Downloads/install_folder/driver/rtl8192EU_linux_v4.2.2_7585.20130524/core/rtw_ioctl_set.o
  CC [M]  /home/ryletti/Downloads/install_folder/driver/rtl8192EU_linux_v4.2.2_7585.20130524/core/rtw_ieee80211.o
  CC [M]  /home/ryletti/Downloads/install_folder/driver/rtl8192EU_linux_v4.2.2_7585.20130524/core/rtw_mlme.o
  CC [M]  /home/ryletti/Downloads/install_folder/driver/rtl8192EU_linux_v4.2.2_7585.20130524/core/rtw_mlme_ext.o
  CC [M]  /home/ryletti/Downloads/install_folder/driver/rtl8192EU_linux_v4.2.2_7585.20130524/core/rtw_wlan_util.o
  CC [M]  /home/ryletti/Downloads/install_folder/driver/rtl8192EU_linux_v4.2.2_7585.20130524/core/rtw_vht.o
  CC [M]  /home/ryletti/Downloads/install_folder/driver/rtl8192EU_linux_v4.2.2_7585.20130524/core/rtw_pwrctrl.o
  CC [M]  /home/ryletti/Downloads/install_folder/driver/rtl8192EU_linux_v4.2.2_7585.20130524/core/rtw_rf.o
  CC [M]  /home/ryletti/Downloads/install_folder/driver/rtl8192EU_linux_v4.2.2_7585.20130524/core/rtw_recv.o
  CC [M]  /home/ryletti/Downloads/install_folder/driver/rtl8192EU_linux_v4.2.2_7585.20130524/core/rtw_sta_mgt.o
  CC [M]  /home/ryletti/Downloads/install_folder/driver/rtl8192EU_linux_v4.2.2_7585.20130524/core/rtw_ap.o
  CC [M]  /home/ryletti/Downloads/install_folder/driver/rtl8192EU_linux_v4.2.2_7585.20130524/core/rtw_xmit.o
  CC [M]  /home/ryletti/Downloads/install_folder/driver/rtl8192EU_linux_v4.2.2_7585.20130524/core/rtw_p2p.o
  CC [M]  /home/ryletti/Downloads/install_folder/driver/rtl8192EU_linux_v4.2.2_7585.20130524/core/rtw_tdls.o
  CC [M]  /home/ryletti/Downloads/install_folder/driver/rtl8192EU_linux_v4.2.2_7585.20130524/core/rtw_br_ext.o
  CC [M]  /home/ryletti/Downloads/install_folder/driver/rtl8192EU_linux_v4.2.2_7585.20130524/core/rtw_iol.o
  CC [M]  /home/ryletti/Downloads/install_folder/driver/rtl8192EU_linux_v4.2.2_7585.20130524/core/rtw_sreset.o
  CC [M]  /home/ryletti/Downloads/install_folder/driver/rtl8192EU_linux_v4.2.2_7585.20130524/core/efuse/rtw_efuse.o
  CC [M]  /home/ryletti/Downloads/install_folder/driver/rtl8192EU_linux_v4.2.2_7585.20130524/os_dep/osdep_service.o
  CC [M]  /home/ryletti/Downloads/install_folder/driver/rtl8192EU_linux_v4.2.2_7585.20130524/os_dep/linux/os_intfs.o
/home/ryletti/Downloads/install_folder/driver/rtl8192EU_linux_v4.2.2_7585.20130524/os_dep/linux/os_intfs.c: In function ‘rtw_proc_init_one’:
/home/ryletti/Downloads/install_folder/driver/rtl8192EU_linux_v4.2.2_7585.20130524/os_dep/linux/os_intfs.c:368:3: warning: passing argument 4 of ‘proc_create_data’ from incompatible pointer type [enabled by default]
   entry = proc_create_data("ver_info", S_IFREG | S_IRUGO, rtw_proc, proc_get_drv_version, dev);       
   ^
In file included from /home/ryletti/Downloads/install_folder/driver/rtl8192EU_linux_v4.2.2_7585.20130524/include/osdep_service_linux.h:55:0,
                 from /home/ryletti/Downloads/install_folder/driver/rtl8192EU_linux_v4.2.2_7585.20130524/include/osdep_service.h:41,
                 from /home/ryletti/Downloads/install_folder/driver/rtl8192EU_linux_v4.2.2_7585.20130524/include/drv_types.h:32,
                 from /home/ryletti/Downloads/install_folder/driver/rtl8192EU_linux_v4.2.2_7585.20130524/os_dep/linux/os_intfs.c:22:
include/linux/proc_fs.h:25:31: note: expected ‘const struct file_operations *’ but argument is of type ‘int (*)(char *, char **, off_t,  int,  int *, void *)’
 extern struct proc_dir_entry *proc_create_data(const char *, umode_t,
                               ^
/home/ryletti/Downloads/install_folder/driver/rtl8192EU_linux_v4.2.2_7585.20130524/os_dep/linux/os_intfs.c:421:8: warning: passing argument 4 of ‘proc_create_data’ from incompatible pointer type [enabled by default]
        dir_dev, proc_get_write_reg, dev);       
        ^
In file included from /home/ryletti/Downloads/install_folder/driver/rtl8192EU_linux_v4.2.2_7585.20130524/include/osdep_service_linux.h:55:0,
                 from /home/ryletti/Downloads/install_folder/driver/rtl8192EU_linux_v4.2.2_7585.20130524/include/osdep_service.h:41,
                 from /home/ryletti/Downloads/install_folder/driver/rtl8192EU_linux_v4.2.2_7585.20130524/include/drv_types.h:32,
                 from /home/ryletti/Downloads/install_folder/driver/rtl8192EU_linux_v4.2.2_7585.20130524/os_dep/linux/os_intfs.c:22:
include/linux/proc_fs.h:25:31: note: expected ‘const struct file_operations *’ but argument is of type ‘int (*)(char *, char **, off_t,  int,  int *, void *)’
 extern struct proc_dir_entry *proc_create_data(const char *, umode_t,
                               ^
/home/ryletti/Downloads/install_folder/driver/rtl8192EU_linux_v4.2.2_7585.20130524/os_dep/linux/os_intfs.c:434:8: warning: passing argument 4 of ‘proc_create_data’ from incompatible pointer type [enabled by default]
        dir_dev, proc_get_read_reg, dev);       
        ^
In file included from /home/ryletti/Downloads/install_folder/driver/rtl8192EU_linux_v4.2.2_7585.20130524/include/osdep_service_linux.h:55:0,
                 from /home/ryletti/Downloads/install_folder/driver/rtl8192EU_linux_v4.2.2_7585.20130524/include/osdep_service.h:41,
                 from /home/ryletti/Downloads/install_folder/driver/rtl8192EU_linux_v4.2.2_7585.20130524/include/drv_types.h:32,
                 from /home/ryletti/Downloads/install_folder/driver/rtl8192EU_linux_v4.2.2_7585.20130524/os_dep/linux/os_intfs.c:22:
include/linux/proc_fs.h:25:31: note: expected ‘const struct file_operations *’ but argument is of type ‘int (*)(char *, char **, off_t,  int,  int *, void *)’
 extern struct proc_dir_entry *proc_create_data(const char *, umode_t,
                               ^
/home/ryletti/Downloads/install_folder/driver/rtl8192EU_linux_v4.2.2_7585.20130524/os_dep/linux/os_intfs.c:447:8: warning: passing argument 4 of ‘proc_create_data’ from incompatible pointer type [enabled by default]
        dir_dev, proc_get_fwstate, dev);       
        ^
In file included from /home/ryletti/Downloads/install_folder/driver/rtl8192EU_linux_v4.2.2_7585.20130524/include/osdep_service_linux.h:55:0,
                 from /home/ryletti/Downloads/install_folder/driver/rtl8192EU_linux_v4.2.2_7585.20130524/include/osdep_service.h:41,
                 from /home/ryletti/Downloads/install_folder/driver/rtl8192EU_linux_v4.2.2_7585.20130524/include/drv_types.h:32,
                 from /home/ryletti/Downloads/install_folder/driver/rtl8192EU_linux_v4.2.2_7585.20130524/os_dep/linux/os_intfs.c:22:
include/linux/proc_fs.h:25:31: note: expected ‘const struct file_operations *’ but argument is of type ‘int (*)(char *, char **, off_t,  int,  int *, void *)’
 extern struct proc_dir_entry *proc_create_data(const char *, umode_t,
                               ^
/home/ryletti/Downloads/install_folder/driver/rtl8192EU_linux_v4.2.2_7585.20130524/os_dep/linux/os_intfs.c:459:8: warning: passing argument 4 of ‘proc_create_data’ from incompatible pointer type [enabled by default]
        dir_dev, proc_get_sec_info, dev);       
        ^
In file included from /home/ryletti/Downloads/install_folder/driver/rtl8192EU_linux_v4.2.2_7585.20130524/include/osdep_service_linux.h:55:0,
                 from /home/ryletti/Downloads/install_folder/driver/rtl8192EU_linux_v4.2.2_7585.20130524/include/osdep_service.h:41,
                 from /home/ryletti/Downloads/install_folder/driver/rtl8192EU_linux_v4.2.2_7585.20130524/include/drv_types.h:32,
                 from /home/ryletti/Downloads/install_folder/driver/rtl8192EU_linux_v4.2.2_7585.20130524/os_dep/linux/os_intfs.c:22:
include/linux/proc_fs.h:25:31: note: expected ‘const struct file_operations *’ but argument is of type ‘int (*)(char *, char **, off_t,  int,  int *, void *)’
 extern struct proc_dir_entry *proc_create_data(const char *, umode_t,
                               ^
/home/ryletti/Downloads/install_folder/driver/rtl8192EU_linux_v4.2.2_7585.20130524/os_dep/linux/os_intfs.c:471:8: warning: passing argument 4 of ‘proc_create_data’ from incompatible pointer type [enabled by default]
        dir_dev, proc_get_mlmext_state, dev);       
        ^
In file included from /home/ryletti/Downloads/install_folder/driver/rtl8192EU_linux_v4.2.2_7585.20130524/include/osdep_service_linux.h:55:0,
                 from /home/ryletti/Downloads/install_folder/driver/rtl8192EU_linux_v4.2.2_7585.20130524/include/osdep_service.h:41,
                 from /home/ryletti/Downloads/install_folder/driver/rtl8192EU_linux_v4.2.2_7585.20130524/include/drv_types.h:32,
                 from /home/ryletti/Downloads/install_folder/driver/rtl8192EU_linux_v4.2.2_7585.20130524/os_dep/linux/os_intfs.c:22:
include/linux/proc_fs.h:25:31: note: expected ‘const struct file_operations *’ but argument is of type ‘int (*)(char *, char **, off_t,  int,  int *, void *)’
 extern struct proc_dir_entry *proc_create_data(const char *, umode_t,
                               ^
/home/ryletti/Downloads/install_folder/driver/rtl8192EU_linux_v4.2.2_7585.20130524/os_dep/linux/os_intfs.c:483:8: warning: passing argument 4 of ‘proc_create_data’ from incompatible pointer type [enabled by default]
        dir_dev, proc_get_qos_option, dev);       
        ^
In file included from /home/ryletti/Downloads/install_folder/driver/rtl8192EU_linux_v4.2.2_7585.20130524/include/osdep_service_linux.h:55:0,
                 from /home/ryletti/Downloads/install_folder/driver/rtl8192EU_linux_v4.2.2_7585.20130524/include/osdep_service.h:41,
                 from /home/ryletti/Downloads/install_folder/driver/rtl8192EU_linux_v4.2.2_7585.20130524/include/drv_types.h:32,
                 from /home/ryletti/Downloads/install_folder/driver/rtl8192EU_linux_v4.2.2_7585.20130524/os_dep/linux/os_intfs.c:22:
include/linux/proc_fs.h:25:31: note: expected ‘const struct file_operations *’ but argument is of type ‘int (*)(char *, char **, off_t,  int,  int *, void *)’
 extern struct proc_dir_entry *proc_create_data(const char *, umode_t,
                               ^
/home/ryletti/Downloads/install_folder/driver/rtl8192EU_linux_v4.2.2_7585.20130524/os_dep/linux/os_intfs.c:495:8: warning: passing argument 4 of ‘proc_create_data’ from incompatible pointer type [enabled by default]
        dir_dev, proc_get_ht_option, dev);       
        ^
In file included from /home/ryletti/Downloads/install_folder/driver/rtl8192EU_linux_v4.2.2_7585.20130524/include/osdep_service_linux.h:55:0,
                 from /home/ryletti/Downloads/install_folder/driver/rtl8192EU_linux_v4.2.2_7585.20130524/include/osdep_service.h:41,
                 from /home/ryletti/Downloads/install_folder/driver/rtl8192EU_linux_v4.2.2_7585.20130524/include/drv_types.h:32,
                 from /home/ryletti/Downloads/install_folder/driver/rtl8192EU_linux_v4.2.2_7585.20130524/os_dep/linux/os_intfs.c:22:
include/linux/proc_fs.h:25:31: note: expected ‘const struct file_operations *’ but argument is of type ‘int (*)(char *, char **, off_t,  int,  int *, void *)’
 extern struct proc_dir_entry *proc_create_data(const char *, umode_t,
                               ^
/home/ryletti/Downloads/install_folder/driver/rtl8192EU_linux_v4.2.2_7585.20130524/os_dep/linux/os_intfs.c:507:8: warning: passing argument 4 of ‘proc_create_data’ from incompatible pointer type [enabled by default]
        dir_dev, proc_get_rf_info, dev);       
        ^
In file included from /home/ryletti/Downloads/install_folder/driver/rtl8192EU_linux_v4.2.2_7585.20130524/include/osdep_service_linux.h:55:0,
                 from /home/ryletti/Downloads/install_folder/driver/rtl8192EU_linux_v4.2.2_7585.20130524/include/osdep_service.h:41,
                 from /home/ryletti/Downloads/install_folder/driver/rtl8192EU_linux_v4.2.2_7585.20130524/include/drv_types.h:32,
                 from /home/ryletti/Downloads/install_folder/driver/rtl8192EU_linux_v4.2.2_7585.20130524/os_dep/linux/os_intfs.c:22:
include/linux/proc_fs.h:25:31: note: expected ‘const struct file_operations *’ but argument is of type ‘int (*)(char *, char **, off_t,  int,  int *, void *)’
 extern struct proc_dir_entry *proc_create_data(const char *, umode_t,
                               ^
/home/ryletti/Downloads/install_folder/driver/rtl8192EU_linux_v4.2.2_7585.20130524/os_dep/linux/os_intfs.c:519:8: warning: passing argument 4 of ‘proc_create_data’ from incompatible pointer type [enabled by default]
        dir_dev, proc_get_ap_info, dev);       
        ^
In file included from /home/ryletti/Downloads/install_folder/driver/rtl8192EU_linux_v4.2.2_7585.20130524/include/osdep_service_linux.h:55:0,
                 from /home/ryletti/Downloads/install_folder/driver/rtl8192EU_linux_v4.2.2_7585.20130524/include/osdep_service.h:41,
                 from /home/ryletti/Downloads/install_folder/driver/rtl8192EU_linux_v4.2.2_7585.20130524/include/drv_types.h:32,
                 from /home/ryletti/Downloads/install_folder/driver/rtl8192EU_linux_v4.2.2_7585.20130524/os_dep/linux/os_intfs.c:22:
include/linux/proc_fs.h:25:31: note: expected ‘const struct file_operations *’ but argument is of type ‘int (*)(char *, char **, off_t,  int,  int *, void *)’
 extern struct proc_dir_entry *proc_create_data(const char *, umode_t,
                               ^
/home/ryletti/Downloads/install_folder/driver/rtl8192EU_linux_v4.2.2_7585.20130524/os_dep/linux/os_intfs.c:531:8: warning: passing argument 4 of ‘proc_create_data’ from incompatible pointer type [enabled by default]
        dir_dev, proc_get_adapter_state, dev);       
        ^
In file included from /home/ryletti/Downloads/install_folder/driver/rtl8192EU_linux_v4.2.2_7585.20130524/include/osdep_service_linux.h:55:0,
                 from /home/ryletti/Downloads/install_folder/driver/rtl8192EU_linux_v4.2.2_7585.20130524/include/osdep_service.h:41,
                 from /home/ryletti/Downloads/install_folder/driver/rtl8192EU_linux_v4.2.2_7585.20130524/include/drv_types.h:32,
                 from /home/ryletti/Downloads/install_folder/driver/rtl8192EU_linux_v4.2.2_7585.20130524/os_dep/linux/os_intfs.c:22:
include/linux/proc_fs.h:25:31: note: expected ‘const struct file_operations *’ but argument is of type ‘int (*)(char *, char **, off_t,  int,  int *, void *)’
 extern struct proc_dir_entry *proc_create_data(const char *, umode_t,
                               ^
/home/ryletti/Downloads/install_folder/driver/rtl8192EU_linux_v4.2.2_7585.20130524/os_dep/linux/os_intfs.c:543:8: warning: passing argument 4 of ‘proc_create_data’ from incompatible pointer type [enabled by default]
        dir_dev, proc_get_trx_info, dev);       
        ^
In file included from /home/ryletti/Downloads/install_folder/driver/rtl8192EU_linux_v4.2.2_7585.20130524/include/osdep_service_linux.h:55:0,
                 from /home/ryletti/Downloads/install_folder/driver/rtl8192EU_linux_v4.2.2_7585.20130524/include/osdep_service.h:41,
                 from /home/ryletti/Downloads/install_folder/driver/rtl8192EU_linux_v4.2.2_7585.20130524/include/drv_types.h:32,
                 from /home/ryletti/Downloads/install_folder/driver/rtl8192EU_linux_v4.2.2_7585.20130524/os_dep/linux/os_intfs.c:22:
include/linux/proc_fs.h:25:31: note: expected ‘const struct file_operations *’ but argument is of type ‘int (*)(char *, char **, off_t,  int,  int *, void *)’
 extern struct proc_dir_entry *proc_create_data(const char *, umode_t,
                               ^
/home/ryletti/Downloads/install_folder/driver/rtl8192EU_linux_v4.2.2_7585.20130524/os_dep/linux/os_intfs.c:554:8: warning: passing argument 4 of ‘proc_create_data’ from incompatible pointer type [enabled by default]
        dir_dev, proc_get_mac_reg_dump1, dev);
        ^
In file included from /home/ryletti/Downloads/install_folder/driver/rtl8192EU_linux_v4.2.2_7585.20130524/include/osdep_service_linux.h:55:0,
                 from /home/ryletti/Downloads/install_folder/driver/rtl8192EU_linux_v4.2.2_7585.20130524/include/osdep_service.h:41,
                 from /home/ryletti/Downloads/install_folder/driver/rtl8192EU_linux_v4.2.2_7585.20130524/include/drv_types.h:32,
                 from /home/ryletti/Downloads/install_folder/driver/rtl8192EU_linux_v4.2.2_7585.20130524/os_dep/linux/os_intfs.c:22:
include/linux/proc_fs.h:25:31: note: expected ‘const struct file_operations *’ but argument is of type ‘int (*)(char *, char **, off_t,  int,  int *, void *)’
 extern struct proc_dir_entry *proc_create_data(const char *, umode_t,
                               ^
/home/ryletti/Downloads/install_folder/driver/rtl8192EU_linux_v4.2.2_7585.20130524/os_dep/linux/os_intfs.c:566:8: warning: passing argument 4 of ‘proc_create_data’ from incompatible pointer type [enabled by default]
        dir_dev, proc_get_mac_reg_dump2, dev);
        ^
In file included from /home/ryletti/Downloads/install_folder/driver/rtl8192EU_linux_v4.2.2_7585.20130524/include/osdep_service_linux.h:55:0,
                 from /home/ryletti/Downloads/install_folder/driver/rtl8192EU_linux_v4.2.2_7585.20130524/include/osdep_service.h:41,
                 from /home/ryletti/Downloads/install_folder/driver/rtl8192EU_linux_v4.2.2_7585.20130524/include/drv_types.h:32,
                 from /home/ryletti/Downloads/install_folder/driver/rtl8192EU_linux_v4.2.2_7585.20130524/os_dep/linux/os_intfs.c:22:
include/linux/proc_fs.h:25:31: note: expected ‘const struct file_operations *’ but argument is of type ‘int (*)(char *, char **, off_t,  int,  int *, void *)’
 extern struct proc_dir_entry *proc_create_data(const char *, umode_t,
                               ^
/home/ryletti/Downloads/install_folder/driver/rtl8192EU_linux_v4.2.2_7585.20130524/os_dep/linux/os_intfs.c:578:8: warning: passing argument 4 of ‘proc_create_data’ from incompatible pointer type [enabled by default]
        dir_dev, proc_get_mac_reg_dump3, dev);
        ^
In file included from /home/ryletti/Downloads/install_folder/driver/rtl8192EU_linux_v4.2.2_7585.20130524/include/osdep_service_linux.h:55:0,
                 from /home/ryletti/Downloads/install_folder/driver/rtl8192EU_linux_v4.2.2_7585.20130524/include/osdep_service.h:41,
                 from /home/ryletti/Downloads/install_folder/driver/rtl8192EU_linux_v4.2.2_7585.20130524/include/drv_types.h:32,
                 from /home/ryletti/Downloads/install_folder/driver/rtl8192EU_linux_v4.2.2_7585.20130524/os_dep/linux/os_intfs.c:22:
include/linux/proc_fs.h:25:31: note: expected ‘const struct file_operations *’ but argument is of type ‘int (*)(char *, char **, off_t,  int,  int *, void *)’
 extern struct proc_dir_entry *proc_create_data(const char *, umode_t,
                               ^
/home/ryletti/Downloads/install_folder/driver/rtl8192EU_linux_v4.2.2_7585.20130524/os_dep/linux/os_intfs.c:590:8: warning: passing argument 4 of ‘proc_create_data’ from incompatible pointer type [enabled by default]
        dir_dev, proc_get_bb_reg_dump1, dev);
        ^
In file included from /home/ryletti/Downloads/install_folder/driver/rtl8192EU_linux_v4.2.2_7585.20130524/include/osdep_service_linux.h:55:0,
                 from /home/ryletti/Downloads/install_folder/driver/rtl8192EU_linux_v4.2.2_7585.20130524/include/osdep_service.h:41,
                 from /home/ryletti/Downloads/install_folder/driver/rtl8192EU_linux_v4.2.2_7585.20130524/include/drv_types.h:32,
                 from /home/ryletti/Downloads/install_folder/driver/rtl8192EU_linux_v4.2.2_7585.20130524/os_dep/linux/os_intfs.c:22:
include/linux/proc_fs.h:25:31: note: expected ‘const struct file_operations *’ but argument is of type ‘int (*)(char *, char **, off_t,  int,  int *, void *)’
 extern struct proc_dir_entry *proc_create_data(const char *, umode_t,
                               ^
/home/ryletti/Downloads/install_folder/driver/rtl8192EU_linux_v4.2.2_7585.20130524/os_dep/linux/os_intfs.c:602:8: warning: passing argument 4 of ‘proc_create_data’ from incompatible pointer type [enabled by default]
        dir_dev, proc_get_bb_reg_dump2, dev);
        ^
In file included from /home/ryletti/Downloads/install_folder/driver/rtl8192EU_linux_v4.2.2_7585.20130524/include/osdep_service_linux.h:55:0,
                 from /home/ryletti/Downloads/install_folder/driver/rtl8192EU_linux_v4.2.2_7585.20130524/include/osdep_service.h:41,
                 from /home/ryletti/Downloads/install_folder/driver/rtl8192EU_linux_v4.2.2_7585.20130524/include/drv_types.h:32,
                 from /home/ryletti/Downloads/install_folder/driver/rtl8192EU_linux_v4.2.2_7585.20130524/os_dep/linux/os_intfs.c:22:
include/linux/proc_fs.h:25:31: note: expected ‘const struct file_operations *’ but argument is of type ‘int (*)(char *, char **, off_t,  int,  int *, void *)’
 extern struct proc_dir_entry *proc_create_data(const char *, umode_t,
                               ^
/home/ryletti/Downloads/install_folder/driver/rtl8192EU_linux_v4.2.2_7585.20130524/os_dep/linux/os_intfs.c:614:8: warning: passing argument 4 of ‘proc_create_data’ from incompatible pointer type [enabled by default]
        dir_dev, proc_get_bb_reg_dump3, dev);
        ^
In file included from /home/ryletti/Downloads/install_folder/driver/rtl8192EU_linux_v4.2.2_7585.20130524/include/osdep_service_linux.h:55:0,
                 from /home/ryletti/Downloads/install_folder/driver/rtl8192EU_linux_v4.2.2_7585.20130524/include/osdep_service.h:41,
                 from /home/ryletti/Downloads/install_folder/driver/rtl8192EU_linux_v4.2.2_7585.20130524/include/drv_types.h:32,
                 from /home/ryletti/Downloads/install_folder/driver/rtl8192EU_linux_v4.2.2_7585.20130524/os_dep/linux/os_intfs.c:22:
include/linux/proc_fs.h:25:31: note: expected ‘const struct file_operations *’ but argument is of type ‘int (*)(char *, char **, off_t,  int,  int *, void *)’
 extern struct proc_dir_entry *proc_create_data(const char *, umode_t,
                               ^
/home/ryletti/Downloads/install_folder/driver/rtl8192EU_linux_v4.2.2_7585.20130524/os_dep/linux/os_intfs.c:626:8: warning: passing argument 4 of ‘proc_create_data’ from incompatible pointer type [enabled by default]
        dir_dev, proc_get_rf_reg_dump1, dev);
        ^
In file included from /home/ryletti/Downloads/install_folder/driver/rtl8192EU_linux_v4.2.2_7585.20130524/include/osdep_service_linux.h:55:0,
                 from /home/ryletti/Downloads/install_folder/driver/rtl8192EU_linux_v4.2.2_7585.20130524/include/osdep_service.h:41,
                 from /home/ryletti/Downloads/install_folder/driver/rtl8192EU_linux_v4.2.2_7585.20130524/include/drv_types.h:32,
                 from /home/ryletti/Downloads/install_folder/driver/rtl8192EU_linux_v4.2.2_7585.20130524/os_dep/linux/os_intfs.c:22:
include/linux/proc_fs.h:25:31: note: expected ‘const struct file_operations *’ but argument is of type ‘int (*)(char *, char **, off_t,  int,  int *, void *)’
 extern struct proc_dir_entry *proc_create_data(const char *, umode_t,
                               ^
/home/ryletti/Downloads/install_folder/driver/rtl8192EU_linux_v4.2.2_7585.20130524/os_dep/linux/os_intfs.c:638:8: warning: passing argument 4 of ‘proc_create_data’ from incompatible pointer type [enabled by default]
        dir_dev, proc_get_rf_reg_dump2, dev);
        ^
In file included from /home/ryletti/Downloads/install_folder/driver/rtl8192EU_linux_v4.2.2_7585.20130524/include/osdep_service_linux.h:55:0,
                 from /home/ryletti/Downloads/install_folder/driver/rtl8192EU_linux_v4.2.2_7585.20130524/include/osdep_service.h:41,
                 from /home/ryletti/Downloads/install_folder/driver/rtl8192EU_linux_v4.2.2_7585.20130524/include/drv_types.h:32,
                 from /home/ryletti/Downloads/install_folder/driver/rtl8192EU_linux_v4.2.2_7585.20130524/os_dep/linux/os_intfs.c:22:
include/linux/proc_fs.h:25:31: note: expected ‘const struct file_operations *’ but argument is of type ‘int (*)(char *, char **, off_t,  int,  int *, void *)’
 extern struct proc_dir_entry *proc_create_data(const char *, umode_t,
                               ^
/home/ryletti/Downloads/install_folder/driver/rtl8192EU_linux_v4.2.2_7585.20130524/os_dep/linux/os_intfs.c:652:9: warning: passing argument 4 of ‘proc_create_data’ from incompatible pointer type [enabled by default]
         dir_dev, proc_get_rf_reg_dump3, dev);
         ^
In file included from /home/ryletti/Downloads/install_folder/driver/rtl8192EU_linux_v4.2.2_7585.20130524/include/osdep_service_linux.h:55:0,
                 from /home/ryletti/Downloads/install_folder/driver/rtl8192EU_linux_v4.2.2_7585.20130524/include/osdep_service.h:41,
                 from /home/ryletti/Downloads/install_folder/driver/rtl8192EU_linux_v4.2.2_7585.20130524/include/drv_types.h:32,
                 from /home/ryletti/Downloads/install_folder/driver/rtl8192EU_linux_v4.2.2_7585.20130524/os_dep/linux/os_intfs.c:22:
include/linux/proc_fs.h:25:31: note: expected ‘const struct file_operations *’ but argument is of type ‘int (*)(char *, char **, off_t,  int,  int *, void *)’
 extern struct proc_dir_entry *proc_create_data(const char *, umode_t,
                               ^
/home/ryletti/Downloads/install_folder/driver/rtl8192EU_linux_v4.2.2_7585.20130524/os_dep/linux/os_intfs.c:664:9: warning: passing argument 4 of ‘proc_create_data’ from incompatible pointer type [enabled by default]
         dir_dev, proc_get_rf_reg_dump4, dev);
         ^
In file included from /home/ryletti/Downloads/install_folder/driver/rtl8192EU_linux_v4.2.2_7585.20130524/include/osdep_service_linux.h:55:0,
                 from /home/ryletti/Downloads/install_folder/driver/rtl8192EU_linux_v4.2.2_7585.20130524/include/osdep_service.h:41,
                 from /home/ryletti/Downloads/install_folder/driver/rtl8192EU_linux_v4.2.2_7585.20130524/include/drv_types.h:32,
                 from /home/ryletti/Downloads/install_folder/driver/rtl8192EU_linux_v4.2.2_7585.20130524/os_dep/linux/os_intfs.c:22:
include/linux/proc_fs.h:25:31: note: expected ‘const struct file_operations *’ but argument is of type ‘int (*)(char *, char **, off_t,  int,  int *, void *)’
 extern struct proc_dir_entry *proc_create_data(const char *, umode_t,
                               ^
/home/ryletti/Downloads/install_folder/driver/rtl8192EU_linux_v4.2.2_7585.20130524/os_dep/linux/os_intfs.c:678:8: warning: passing argument 4 of ‘proc_create_data’ from incompatible pointer type [enabled by default]
        dir_dev, proc_get_all_sta_info, dev);
        ^
In file included from /home/ryletti/Downloads/install_folder/driver/rtl8192EU_linux_v4.2.2_7585.20130524/include/osdep_service_linux.h:55:0,
                 from /home/ryletti/Downloads/install_folder/driver/rtl8192EU_linux_v4.2.2_7585.20130524/include/osdep_service.h:41,
                 from /home/ryletti/Downloads/install_folder/driver/rtl8192EU_linux_v4.2.2_7585.20130524/include/drv_types.h:32,
                 from /home/ryletti/Downloads/install_folder/driver/rtl8192EU_linux_v4.2.2_7585.20130524/os_dep/linux/os_intfs.c:22:
include/linux/proc_fs.h:25:31: note: expected ‘const struct file_operations *’ but argument is of type ‘int (*)(char *, char **, off_t,  int,  int *, void *)’
 extern struct proc_dir_entry *proc_create_data(const char *, umode_t,
                               ^
/home/ryletti/Downloads/install_folder/driver/rtl8192EU_linux_v4.2.2_7585.20130524/os_dep/linux/os_intfs.c:706:8: warning: passing argument 4 of ‘proc_create_data’ from incompatible pointer type [enabled by default]
        dir_dev, proc_get_best_channel, dev);
        ^
In file included from /home/ryletti/Downloads/install_folder/driver/rtl8192EU_linux_v4.2.2_7585.20130524/include/osdep_service_linux.h:55:0,
                 from /home/ryletti/Downloads/install_folder/driver/rtl8192EU_linux_v4.2.2_7585.20130524/include/osdep_service.h:41,
                 from /home/ryletti/Downloads/install_folder/driver/rtl8192EU_linux_v4.2.2_7585.20130524/include/drv_types.h:32,
                 from /home/ryletti/Downloads/install_folder/driver/rtl8192EU_linux_v4.2.2_7585.20130524/os_dep/linux/os_intfs.c:22:
include/linux/proc_fs.h:25:31: note: expected ‘const struct file_operations *’ but argument is of type ‘int (*)(char *, char **, off_t,  int,  int *, void *)’
 extern struct proc_dir_entry *proc_create_data(const char *, umode_t,
                               ^
/home/ryletti/Downloads/install_folder/driver/rtl8192EU_linux_v4.2.2_7585.20130524/os_dep/linux/os_intfs.c:718:8: warning: passing argument 4 of ‘proc_create_data’ from incompatible pointer type [enabled by default]
        dir_dev, proc_get_rx_signal, dev);
        ^
In file included from /home/ryletti/Downloads/install_folder/driver/rtl8192EU_linux_v4.2.2_7585.20130524/include/osdep_service_linux.h:55:0,
                 from /home/ryletti/Downloads/install_folder/driver/rtl8192EU_linux_v4.2.2_7585.20130524/include/osdep_service.h:41,
                 from /home/ryletti/Downloads/install_folder/driver/rtl8192EU_linux_v4.2.2_7585.20130524/include/drv_types.h:32,
                 from /home/ryletti/Downloads/install_folder/driver/rtl8192EU_linux_v4.2.2_7585.20130524/os_dep/linux/os_intfs.c:22:
include/linux/proc_fs.h:25:31: note: expected ‘const struct file_operations *’ but argument is of type ‘int (*)(char *, char **, off_t,  int,  int *, void *)’
 extern struct proc_dir_entry *proc_create_data(const char *, umode_t,
                               ^
/home/ryletti/Downloads/install_folder/driver/rtl8192EU_linux_v4.2.2_7585.20130524/os_dep/linux/os_intfs.c:733:8: warning: passing argument 4 of ‘proc_create_data’ from incompatible pointer type [enabled by default]
        dir_dev, proc_get_ht_enable, dev);
        ^
In file included from /home/ryletti/Downloads/install_folder/driver/rtl8192EU_linux_v4.2.2_7585.20130524/include/osdep_service_linux.h:55:0,
                 from /home/ryletti/Downloads/install_folder/driver/rtl8192EU_linux_v4.2.2_7585.20130524/include/osdep_service.h:41,
                 from /home/ryletti/Downloads/install_folder/driver/rtl8192EU_linux_v4.2.2_7585.20130524/include/drv_types.h:32,
                 from /home/ryletti/Downloads/install_folder/driver/rtl8192EU_linux_v4.2.2_7585.20130524/os_dep/linux/os_intfs.c:22:
include/linux/proc_fs.h:25:31: note: expected ‘const struct file_operations *’ but argument is of type ‘int (*)(char *, char **, off_t,  int,  int *, void *)’
 extern struct proc_dir_entry *proc_create_data(const char *, umode_t,
                               ^
/home/ryletti/Downloads/install_folder/driver/rtl8192EU_linux_v4.2.2_7585.20130524/os_dep/linux/os_intfs.c:747:8: warning: passing argument 4 of ‘proc_create_data’ from incompatible pointer type [enabled by default]
        dir_dev, proc_get_bw_mode, dev);
        ^
In file included from /home/ryletti/Downloads/install_folder/driver/rtl8192EU_linux_v4.2.2_7585.20130524/include/osdep_service_linux.h:55:0,
                 from /home/ryletti/Downloads/install_folder/driver/rtl8192EU_linux_v4.2.2_7585.20130524/include/osdep_service.h:41,
                 from /home/ryletti/Downloads/install_folder/driver/rtl8192EU_linux_v4.2.2_7585.20130524/include/drv_types.h:32,
                 from /home/ryletti/Downloads/install_folder/driver/rtl8192EU_linux_v4.2.2_7585.20130524/os_dep/linux/os_intfs.c:22:
include/linux/proc_fs.h:25:31: note: expected ‘const struct file_operations *’ but argument is of type ‘int (*)(char *, char **, off_t,  int,  int *, void *)’
 extern struct proc_dir_entry *proc_create_data(const char *, umode_t,
                               ^
/home/ryletti/Downloads/install_folder/driver/rtl8192EU_linux_v4.2.2_7585.20130524/os_dep/linux/os_intfs.c:761:8: warning: passing argument 4 of ‘proc_create_data’ from incompatible pointer type [enabled by default]
        dir_dev, proc_get_ampdu_enable, dev);
        ^
In file included from /home/ryletti/Downloads/install_folder/driver/rtl8192EU_linux_v4.2.2_7585.20130524/include/osdep_service_linux.h:55:0,
                 from /home/ryletti/Downloads/install_folder/driver/rtl8192EU_linux_v4.2.2_7585.20130524/include/osdep_service.h:41,
                 from /home/ryletti/Downloads/install_folder/driver/rtl8192EU_linux_v4.2.2_7585.20130524/include/drv_types.h:32,
                 from /home/ryletti/Downloads/install_folder/driver/rtl8192EU_linux_v4.2.2_7585.20130524/os_dep/linux/os_intfs.c:22:
include/linux/proc_fs.h:25:31: note: expected ‘const struct file_operations *’ but argument is of type ‘int (*)(char *, char **, off_t,  int,  int *, void *)’
 extern struct proc_dir_entry *proc_create_data(const char *, umode_t,
                               ^
/home/ryletti/Downloads/install_folder/driver/rtl8192EU_linux_v4.2.2_7585.20130524/os_dep/linux/os_intfs.c:775:8: warning: passing argument 4 of ‘proc_create_data’ from incompatible pointer type [enabled by default]
        dir_dev, proc_get_rx_stbc, dev);
        ^
In file included from /home/ryletti/Downloads/install_folder/driver/rtl8192EU_linux_v4.2.2_7585.20130524/include/osdep_service_linux.h:55:0,
                 from /home/ryletti/Downloads/install_folder/driver/rtl8192EU_linux_v4.2.2_7585.20130524/include/osdep_service.h:41,
                 from /home/ryletti/Downloads/install_folder/driver/rtl8192EU_linux_v4.2.2_7585.20130524/include/drv_types.h:32,
                 from /home/ryletti/Downloads/install_folder/driver/rtl8192EU_linux_v4.2.2_7585.20130524/os_dep/linux/os_intfs.c:22:
include/linux/proc_fs.h:25:31: note: expected ‘const struct file_operations *’ but argument is of type ‘int (*)(char *, char **, off_t,  int,  int *, void *)’
 extern struct proc_dir_entry *proc_create_data(const char *, umode_t,
                               ^
/home/ryletti/Downloads/install_folder/driver/rtl8192EU_linux_v4.2.2_7585.20130524/os_dep/linux/os_intfs.c:790:6: warning: passing argument 4 of ‘proc_create_data’ from incompatible pointer type [enabled by default]
      dir_dev, proc_get_two_path_rssi, dev);
      ^
In file included from /home/ryletti/Downloads/install_folder/driver/rtl8192EU_linux_v4.2.2_7585.20130524/include/osdep_service_linux.h:55:0,
                 from /home/ryletti/Downloads/install_folder/driver/rtl8192EU_linux_v4.2.2_7585.20130524/include/osdep_service.h:41,
                 from /home/ryletti/Downloads/install_folder/driver/rtl8192EU_linux_v4.2.2_7585.20130524/include/drv_types.h:32,
                 from /home/ryletti/Downloads/install_folder/driver/rtl8192EU_linux_v4.2.2_7585.20130524/os_dep/linux/os_intfs.c:22:
include/linux/proc_fs.h:25:31: note: expected ‘const struct file_operations *’ but argument is of type ‘int (*)(char *, char **, off_t,  int,  int *, void *)’
 extern struct proc_dir_entry *proc_create_data(const char *, umode_t,
                               ^
/home/ryletti/Downloads/install_folder/driver/rtl8192EU_linux_v4.2.2_7585.20130524/os_dep/linux/os_intfs.c:797:8: warning: passing argument 4 of ‘proc_create_data’ from incompatible pointer type [enabled by default]
        dir_dev, proc_get_rssi_disp, dev);
        ^
In file included from /home/ryletti/Downloads/install_folder/driver/rtl8192EU_linux_v4.2.2_7585.20130524/include/osdep_service_linux.h:55:0,
                 from /home/ryletti/Downloads/install_folder/driver/rtl8192EU_linux_v4.2.2_7585.20130524/include/osdep_service.h:41,
                 from /home/ryletti/Downloads/install_folder/driver/rtl8192EU_linux_v4.2.2_7585.20130524/include/drv_types.h:32,
                 from /home/ryletti/Downloads/install_folder/driver/rtl8192EU_linux_v4.2.2_7585.20130524/os_dep/linux/os_intfs.c:22:
include/linux/proc_fs.h:25:31: note: expected ‘const struct file_operations *’ but argument is of type ‘int (*)(char *, char **, off_t,  int,  int *, void *)’
 extern struct proc_dir_entry *proc_create_data(const char *, umode_t,
                               ^
/home/ryletti/Downloads/install_folder/driver/rtl8192EU_linux_v4.2.2_7585.20130524/os_dep/linux/os_intfs.c:829:8: warning: passing argument 4 of ‘proc_create_data’ from incompatible pointer type [enabled by default]
        dir_dev, proc_get_sreset, dev);
        ^
In file included from /home/ryletti/Downloads/install_folder/driver/rtl8192EU_linux_v4.2.2_7585.20130524/include/osdep_service_linux.h:55:0,
                 from /home/ryletti/Downloads/install_folder/driver/rtl8192EU_linux_v4.2.2_7585.20130524/include/osdep_service.h:41,
                 from /home/ryletti/Downloads/install_folder/driver/rtl8192EU_linux_v4.2.2_7585.20130524/include/drv_types.h:32,
                 from /home/ryletti/Downloads/install_folder/driver/rtl8192EU_linux_v4.2.2_7585.20130524/os_dep/linux/os_intfs.c:22:
include/linux/proc_fs.h:25:31: note: expected ‘const struct file_operations *’ but argument is of type ‘int (*)(char *, char **, off_t,  int,  int *, void *)’
 extern struct proc_dir_entry *proc_create_data(const char *, umode_t,
                               ^
/home/ryletti/Downloads/install_folder/driver/rtl8192EU_linux_v4.2.2_7585.20130524/os_dep/linux/os_intfs.c: At top level:
/home/ryletti/Downloads/install_folder/driver/rtl8192EU_linux_v4.2.2_7585.20130524/os_dep/linux/os_intfs.c:1216:2: warning: initialization from incompatible pointer type [enabled by default]
  .ndo_select_queue = rtw_select_queue,
  ^
/home/ryletti/Downloads/install_folder/driver/rtl8192EU_linux_v4.2.2_7585.20130524/os_dep/linux/os_intfs.c:1216:2: warning: (near initialization for ‘rtw_netdev_ops.ndo_select_queue’) [enabled by default]
  CC [M]  /home/ryletti/Downloads/install_folder/driver/rtl8192EU_linux_v4.2.2_7585.20130524/os_dep/linux/usb_intf.o
  CC [M]  /home/ryletti/Downloads/install_folder/driver/rtl8192EU_linux_v4.2.2_7585.20130524/os_dep/linux/usb_ops_linux.o
  CC [M]  /home/ryletti/Downloads/install_folder/driver/rtl8192EU_linux_v4.2.2_7585.20130524/os_dep/linux/ioctl_linux.o
/home/ryletti/Downloads/install_folder/driver/rtl8192EU_linux_v4.2.2_7585.20130524/os_dep/linux/ioctl_linux.c: In function ‘rtw_mp_efuse_get’:
/home/ryletti/Downloads/install_folder/driver/rtl8192EU_linux_v4.2.2_7585.20130524/os_dep/linux/ioctl_linux.c:8965:65: warning: iteration 16u invokes undefined behavior [-Waggressive-loop-optimizations]
     sprintf(extra, "%s%02X ", extra, pEfuseHal->fakeEfuseInitMap[i+j]);
                                                                 ^
/home/ryletti/Downloads/install_folder/driver/rtl8192EU_linux_v4.2.2_7585.20130524/os_dep/linux/ioctl_linux.c:8953:3: note: containing loop
   for (i = 0; i < EFUSE_MAP_SIZE; i += 16)
   ^
/home/ryletti/Downloads/install_folder/driver/rtl8192EU_linux_v4.2.2_7585.20130524/os_dep/linux/ioctl_linux.c:9379:69: warning: iteration 16u invokes undefined behavior [-Waggressive-loop-optimizations]
     sprintf(extra, "%s%02X ", extra, pEfuseHal->fakeEfuseModifiedMap[i+j]);
                                                                     ^
/home/ryletti/Downloads/install_folder/driver/rtl8192EU_linux_v4.2.2_7585.20130524/os_dep/linux/ioctl_linux.c:9373:3: note: containing loop
   for (i=0; i<EFUSE_MAP_SIZE; i+=16)
   ^
  CC [M]  /home/ryletti/Downloads/install_folder/driver/rtl8192EU_linux_v4.2.2_7585.20130524/os_dep/linux/xmit_linux.o
  CC [M]  /home/ryletti/Downloads/install_folder/driver/rtl8192EU_linux_v4.2.2_7585.20130524/os_dep/linux/mlme_linux.o
  CC [M]  /home/ryletti/Downloads/install_folder/driver/rtl8192EU_linux_v4.2.2_7585.20130524/os_dep/linux/recv_linux.o
  CC [M]  /home/ryletti/Downloads/install_folder/driver/rtl8192EU_linux_v4.2.2_7585.20130524/os_dep/linux/ioctl_cfg80211.o
  CC [M]  /home/ryletti/Downloads/install_folder/driver/rtl8192EU_linux_v4.2.2_7585.20130524/os_dep/linux/rtw_android.o
/home/ryletti/Downloads/install_folder/driver/rtl8192EU_linux_v4.2.2_7585.20130524/os_dep/linux/rtw_android.c: In function ‘rtw_android_cmdstr_to_num’:
/home/ryletti/Downloads/install_folder/driver/rtl8192EU_linux_v4.2.2_7585.20130524/os_dep/linux/rtw_android.c:227:3: error: implicit declaration of function ‘strnicmp’ [-Werror=implicit-function-declaration]
   if(0 == strnicmp(cmdstr , android_wifi_cmd_str[cmd_num], strlen(android_wifi_cmd_str[cmd_num])) )
   ^
/home/ryletti/Downloads/install_folder/driver/rtl8192EU_linux_v4.2.2_7585.20130524/os_dep/linux/rtw_android.c: In function ‘rtw_android_priv_cmd’:
/home/ryletti/Downloads/install_folder/driver/rtl8192EU_linux_v4.2.2_7585.20130524/os_dep/linux/rtw_android.c:356:30: warning: cast to pointer from integer of different size [-Wint-to-pointer-cast]
  if (copy_from_user(command, (void *)priv_cmd.buf, priv_cmd.total_len)) {
                              ^
/home/ryletti/Downloads/install_folder/driver/rtl8192EU_linux_v4.2.2_7585.20130524/os_dep/linux/rtw_android.c:548:4: warning: passing argument 1 of ‘get_int_from_command’ makes pointer from integer without a cast [enabled by default]
    pwfd_info->rtsp_ctrlport = ( u16 ) get_int_from_command( priv_cmd.buf );
    ^
/home/ryletti/Downloads/install_folder/driver/rtl8192EU_linux_v4.2.2_7585.20130524/os_dep/linux/rtw_android.c:307:5: note: expected ‘char *’ but argument is of type ‘compat_uptr_t’
 int get_int_from_command( char* pcmd )
     ^
/home/ryletti/Downloads/install_folder/driver/rtl8192EU_linux_v4.2.2_7585.20130524/os_dep/linux/rtw_android.c:568:4: warning: passing argument 1 of ‘get_int_from_command’ makes pointer from integer without a cast [enabled by default]
    pwfd_info->wfd_device_type = ( u8 ) get_int_from_command( priv_cmd.buf );
    ^
/home/ryletti/Downloads/install_folder/driver/rtl8192EU_linux_v4.2.2_7585.20130524/os_dep/linux/rtw_android.c:307:5: note: expected ‘char *’ but argument is of type ‘compat_uptr_t’
 int get_int_from_command( char* pcmd )
     ^
/home/ryletti/Downloads/install_folder/driver/rtl8192EU_linux_v4.2.2_7585.20130524/os_dep/linux/rtw_android.c:592:20: warning: cast to pointer from integer of different size [-Wint-to-pointer-cast]
   if (copy_to_user((void *)priv_cmd.buf, command, bytes_written)) {
                    ^
cc1: some warnings being treated as errors
make[2]: *** [/home/ryletti/Downloads/install_folder/driver/rtl8192EU_linux_v4.2.2_7585.20130524/os_dep/linux/rtw_android.o] Error 1
make[1]: *** [_module_/home/ryletti/Downloads/install_folder/driver/rtl8192EU_linux_v4.2.2_7585.20130524] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-4.2.0-35-generic'
make: *** [modules] Error 2
##################################################
Compile make driver error: 2
Please check error Mesg
##################################################

```

---

### Post by enkill3 on 2016-04-06
never mind, Desperation wins out. here is the fix if anyone else can't make it work

[COLOR=#000000][I]sudo gedit /etc/udev/rules.d/network_drivers.rules
[/I]
[/COLOR]
[COLOR=#000000]and add this line:[/COLOR]
[COLOR=#000000][I]ACTION=="add", SUBSYSTEM=="usb", ATTR{idVendor}=="050d", ATTR{idProduct}=="945a", RUN+="/sbin/modprobe -qba r8192s_usb"
[/I]
[/COLOR]
[COLOR=#000000]Save it then run this command to open the second file:[/COLOR]
[COLOR=#000000][I]sudo gedit /etc/modprobe.d/network_drivers.conf
[/I]
[/COLOR]
[COLOR=#000000]and add this line:[/COLOR]
[COLOR=#000000][I]install r8192s_usb /sbin/modprobe --ignore-install r8192s_usb $CMDLINE_OPTS; /bin/echo "050d 945a" > /sys/bus/usb/drivers/rtl819xU/new_id
[/I]
[/COLOR]

[COLOR=#000000]2.) Then I obtained the firmware from here:[/COLOR]
[COLOR=#000000][I]"http://launchpadlibrarian.net/37387612/rtl8192sfw.bin.gz"
[/I]
[/COLOR]
[COLOR=#000000]and copied it to /lib/firmware/RTL8192SU/ with these commands:[/COLOR]

[COLOR=#000000][I]wget "http://launchpadlibrarian.net/37387612/rtl8192sfw.bin.gz"
gunzip rtl8192sfw.bin.gz 
sudo mkdir /lib/firmware/RTL8192SU
sudo cp rtl8192sfw.bin /lib/firmware/RTL8192SU


[/I]
[/COLOR]
[COLOR=#000000][/COLOR]

---

### Post by enkill3 on 2016-06-06
May as well add this onto here instead of creating another post, 
Updated to 16.4 and unsurprisingly have a new issue!
For some reason i am unable to save files with geddit. i get the below error,
anyone have any ideas?


```
~$ sudo gedit /etc/udev/rules.d/network_drivers.rules

** (gedit:3223): WARNING **: Set document metadata failed: Setting attribute metadata::gedit-spell-enabled not supported

** (gedit:3223): WARNING **: Set document metadata failed: Setting attribute metadata::gedit-encoding not supported

** (gedit:3223): WARNING **: Set document metadata failed: Setting attribute metadata::gedit-position not supported
[COLOR=#000000][/COLOR]
```

---

