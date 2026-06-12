---
title: "Driver compilation problem for Dynamode WL-AC-600M USB dongle"
date: 2017-07-21
forum: General Help
---

### Post by jet-bundle on 2017-07-21
I have an HP Pavilion TS11 laptop, and have had problems with the driver for its wireless card (see [https://ubuntuforums.org/showthread.php?t=2365838](https://ubuntuforums.org/showthread.php?t=2365838)). Trying another approach, I've bought a dongle but I'm having problems installing the driver. (The software came on a CD in the pack.) Here is install.sh```
#!/bin/bash
# Auto install for 8192cu
# September, 1 2010 v1.0.0, willisTang
# 
# Add make_drv to select chip type
# Novembor, 21 2011 v1.1.0, Jeff Hung
################################################################################
echo "##################################################"
echo "Realtek Wi-Fi driver Auto installation script"
echo "Novembor, 21 2011 v1.1.0"
echo "##################################################"
################################################################################
#   Decompress the driver source tal ball
################################################################################
cd driver
Drvfoulder=`ls |grep .tar.gz`
echo "Decompress the driver source tar ball:"
echo " "$Drvfoulder
tar zxvf $Drvfoulder
Drvfoulder=`ls |grep -iv '.tar.gz'`
echo "$Drvfoulder"
cd  $Drvfoulder
################################################################################
#   If makd_drv exixt, execute it to select chip type
################################################################################
if [ -e ./make_drv ]; then
 ./make_drv
fi
################################################################################
#                       make clean
################################################################################
echo "Authentication requested [root] for make clean:"
if [ "`uname -r |grep fc`" == " " ]; then
        sudo su -c "make clean"; Error=$?
else
        su -c "make clean"; Error=$?
fi
################################################################################
#   Compile the driver
################################################################################
echo "Authentication requested [root] for make driver:"
if [ "`uname -r |grep fc`" == " " ]; then
 sudo su -c make; Error=$?
else 
 su -c make; Error=$?
fi
################################################################################
#   Check whether or not the driver compilation is done
################################################################################
module=`ls |grep -i 'ko'`
echo "##################################################"
if [ "$Error" != 0 ];then
 echo "Compile make driver error: $Error"
 echo "Please check error Mesg"
 echo "##################################################"
 exit
else
 echo "Compile make driver ok!!" 
 echo "##################################################"
fi
if [ "`uname -r |grep fc`" == " " ]; then
 echo "Authentication requested [root] for remove driver:"
 sudo su -c "rmmod $module"
 echo "Authentication requested [root] for insert driver:"
 sudo su -c "insmod $module"
 echo "Authentication requested [root] for install driver:"
 sudo su -c "make install"
else
 echo "Authentication requested [root] for remove driver:"
 su -c "rmmod $module"
 echo "Authentication requested [root] for insert driver:"
 su -c "insmod $module"
 echo "Authentication requested [root] for install driver:"
 su -c "make install"
fi
echo "##################################################"
echo "The Setup Script is completed !"
echo "##################################################"
 

``` Here is the result: ```
##################################################
Realtek Wi-Fi driver Auto installation script
Novembor, 21 2011 v1.1.0
##################################################
Decompress the driver source tar ball:
 rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51.tar.gz
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/core/
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/core/rtw_mp.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/core/rtw_ioctl_query.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/core/rtw_wapi_sms4.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/core/rtw_ioctl_rtl.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/core/rtw_wapi.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/core/efuse/
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/core/efuse/rtw_efuse.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/core/rtw_mlme_ext.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/core/rtw_sta_mgt.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/core/rtw_io.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/core/rtw_rf.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/core/rtw_xmit.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/core/rtw_vht.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/core/rtw_ioctl_set.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/core/rtw_iol.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/core/rtw_odm.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/core/rtw_cmd.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/core/rtw_ap.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/core/rtw_pwrctrl.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/core/rtw_tdls.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/core/rtw_bt_mp.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/core/rtw_eeprom.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/core/rtw_debug.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/core/rtw_beamforming.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/core/rtw_wlan_util.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/core/rtw_mlme.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/core/rtw_p2p.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/core/rtw_sreset.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/core/rtw_btcoex.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/core/rtw_mp_ioctl.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/core/rtw_ieee80211.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/core/rtw_recv.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/core/rtw_br_ext.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/core/rtw_mem.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/core/rtw_security.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/osdep_service_xp.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtw_br_ext.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/drv_types_pci.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtl8192e_spec.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtl8192c_cmd.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/drv_types.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtl8812a_led.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/mp_custom_oid.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/Hal8192DPhyCfg.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtw_vht.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtl8192e_sreset.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtl8192c_spec.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtl8192e_recv.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtw_iol.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtw_xmit.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/Hal8723BPhyReg.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/usb_hal.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/drv_types_gspi.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtl8192d_xmit.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtl8188e_hal.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtl8812a_rf.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/osdep_service_ce.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtl8723b_sreset.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtl8192e_cmd.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/usb_ops_linux.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtl8723b_rf.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/byteorder/
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/byteorder/swabb.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/byteorder/little_endian.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/byteorder/big_endian.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/byteorder/swab.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/byteorder/generic.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/Hal8723BPwrSeq.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/drv_types_ce.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtw_io.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/ieee80211.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtl8192e_xmit.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/Hal8821APwrSeq.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtl8723a_sreset.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/drv_conf.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/ip.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/osdep_service_linux.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtw_wifi_regd.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/hal_gspi.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/sdio_ops_xp.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/usb_vendor_req.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtw_efuse.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtl8821a_xmit.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/Hal8192DPhyReg.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/drv_types_xp.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/hal_com_led.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtw_mlme_ext.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtl8192c_sreset.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtl8821a_spec.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtw_android.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtl8723a_spec.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/xmit_osdep.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/sdio_osintf.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/Hal8188EPhyReg.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtl8723a_hal.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtl8723b_cmd.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/Hal8723APhyCfg.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/Hal8812PhyReg.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/hal_com_reg.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/autoconf.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/pci_osintf.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtl8188e_xmit.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtw_cmd.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/hal_com.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/sdio_ops_ce.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtl8188e_led.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtl8812a_dm.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtl8192e_hal.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/Hal8192EPwrSeq.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtw_ioctl_query.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtw_wapi.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtl8188e_cmd.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtw_ioctl.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtl8192d_rf.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/wifi.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/Hal8192CPhyCfg.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtw_version.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/Hal8192EPhyCfg.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtl8192c_dm.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/if_ether.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtw_mlme.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtw_debug.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtl8723a_rf.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/gspi_ops_linux.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/hal_sdio.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/mlme_osdep.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtl8192e_dm.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtw_beamforming.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtl8812a_hal.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtl8723a_pg.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/hal_data.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/pci_hal.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/circ_buf.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtl8192d_dm.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/HalPwrSeqCmd.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtw_byteorder.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/nic_spec.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtl8723a_dm.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtl8192d_hal.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/hal_btcoex.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/Hal8192EPhyReg.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/wlan_bssdef.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtw_p2p.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtl8192e_led.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtl8723a_xmit.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/Hal8723BPhyCfg.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtl8812a_cmd.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtl8192c_led.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/custom_gpio.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/ethernet.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtl8723b_hal.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtw_ioctl_rtl.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/gspi_ops.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtl8188e_sreset.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtw_event.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/sdio_ops_linux.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/linux/
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/linux/wireless.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/osdep_service.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/drv_types_sdio.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtl8192e_rf.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtl8723b_led.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtw_qos.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/hal_com_phycfg.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtl8192d_spec.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/ieee80211_ext.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtl8192c_event.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtw_ap.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/hal_phy.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/recv_osdep.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtl8192c_hal.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtw_pwrctrl.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtl8192d_recv.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtl8723b_dm.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/sdio_ops.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtl8188e_dm.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/gspi_hal.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtw_odm.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/usb_ops.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/hal_com_h2c.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/usb_osintf.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/Hal8812PhyCfg.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtl8192c_rf.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtl8812a_xmit.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/sdio_hal.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/hal_pg.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/hal_phy_reg.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtw_mem.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtl8192c_recv.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtw_mp_ioctl.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtw_tdls.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/Hal8812PwrSeq.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/Hal8192CPhyReg.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtl8192d_cmd.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtl8812a_spec.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtl8723b_recv.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtw_ioctl_set.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/basic_types.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtw_bt_mp.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/Hal8188EPhyCfg.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/drv_types_linux.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtw_eeprom.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtl8723b_xmit.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtl8188e_rf.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtw_rf.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtw_recv.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/Hal8723PwrSeq.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/h2clbk.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtl8723b_spec.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/Hal8188EPwrSeq.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtl8723a_cmd.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/pci_ops.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtw_ht.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/osdep_intf.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtw_mp_phy_regdef.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtl8723a_led.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/cmd_osdep.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtw_mp.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtl8812a_recv.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtw_security.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtl8188e_recv.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/osdep_service_bsd.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtl8192c_xmit.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtw_btcoex.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtl8188e_spec.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/HalVerDef.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtl8812a_sreset.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/gspi_osintf.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/sta_info.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtw_sreset.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/hal_intf.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtl8192d_led.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/Hal8723APhyReg.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/include/rtl8723a_recv.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/runwpa
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/clean
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/Kconfig
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/ifcfg-wlan0
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/Makefile
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/wlan0dhcp
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/hal_dm.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/hal_hci/
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/hal_hci/hal_usb.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/efuse/
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/efuse/rtl8812a/
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/efuse/rtl8812a/HalEfuseMask8812A_USB.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/efuse/rtl8812a/HalEfuseMask8821A_PCIE.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/efuse/rtl8812a/HalEfuseMask8812A_PCIE.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/efuse/rtl8812a/HalEfuseMask8821A_USB.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/efuse/rtl8812a/HalEfuseMask8812A_USB.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/efuse/rtl8812a/HalEfuseMask8821A_USB.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/efuse/rtl8812a/HalEfuseMask8812A_PCIE.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/efuse/rtl8812a/HalEfuseMask8821A_PCIE.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/efuse/efuse_mask.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/hal_dm.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/PhyDM_Adaptivity.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/phydm_AntDiv.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/phydm_RaInfo.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/PhyDM_Adaptivity.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/phydm_PathDiv.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/phydm_ACS.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/phydm_DynamicBBPowerSaving.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/phydm_EdcaTurboCheck.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/phydm_NoiseMonitor.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/phydm_interface.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/phydm_PowerTracking.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/HalPhyRf.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/phydm_DynamicBBPowerSaving.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/rtl8812a/
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/rtl8812a/phydm_RTL8812A.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/rtl8812a/HalHWImg8812A_MAC.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/rtl8812a/Mp_Precomp.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/rtl8812a/phydm_RTL8812A.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/rtl8812a/HalHWImg8812A_BB.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/rtl8812a/HalHWImg8812A_FW.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/rtl8812a/phydm_RegConfig8812A.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/rtl8812a/HalHWImg8812A_RF.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/rtl8812a/HalPhyRf_8812A.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/rtl8812a/HalPhyRf_8812A.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/rtl8812a/phydm_RegConfig8812A.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/rtl8812a/HalHWImg8812A_BB.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/rtl8812a/HalHWImg8812A_RF.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/rtl8812a/HalHWImg8812A_FW.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/rtl8812a/HalHWImg8812A_MAC.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/phydm_AntDiv.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/phydm_precomp.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/phydm_NoiseMonitor.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/phydm_debug.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/Mp_Precomp.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/phydm_DynamicTxPower.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/phydm_types.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/phydm_RegDefine11N.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/phydm_RXHP.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/phydm_RaInfo.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/phydm_PowerTracking.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/phydm_AntDect.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/phydm_pre_define.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/phydm_RegDefine11AC.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/rtl8821a/
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/rtl8821a/phydm_RTL8821A.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/rtl8821a/HalHWImg8821A_RF.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/rtl8821a/phydm_RegConfig8821A.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/rtl8821a/phydm_RegConfig8821A.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/rtl8821a/Mp_Precomp.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/rtl8821a/phydm_RTL8821A.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/rtl8821a/HalHWImg8821A_RF.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/rtl8821a/HalHWImg8821A_FW.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/rtl8821a/HalHWImg8821A_MAC.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/rtl8821a/HalHWImg8821A_MAC.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/rtl8821a/PhyDM_IQK_8821A.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/rtl8821a/HalPhyRf_8821A.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/rtl8821a/HalHWImg8821A_BB.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/rtl8821a/HalHWImg8821A_FW.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/rtl8821a/HalPhyRf_8821A.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/rtl8821a/HalHWImg8821A_BB.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/rtl8821a/PhyDM_IQK_8821A.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/phydm_reg.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/phydm_AntDect.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/phydm_ACS.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/phydm_debug.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/HalPhyRf.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/phydm_DIG.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/phydm_DIG.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/phydm_HWConfig.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/phydm_CfoTracking.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/phydm_HWConfig.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/phydm.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/phydm_RXHP.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/phydm_interface.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/phydm_DynamicTxPower.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/phydm_EdcaTurboCheck.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/phydm_CfoTracking.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/phydm.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC/phydm_PathDiv.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/led/
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/led/hal_usb_led.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/rtl8812a/
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/rtl8812a/rtl8812a_xmit.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/rtl8812a/rtl8812a_hal_init.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/rtl8812a/rtl8812a_rxdesc.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/rtl8812a/Hal8821APwrSeq.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/rtl8812a/rtl8812a_rf6052.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/rtl8812a/Hal8812PwrSeq.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/rtl8812a/rtl8812a_cmd.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/rtl8812a/rtl8812a_dm.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/rtl8812a/rtl8812a_sreset.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/rtl8812a/rtl8812a_phycfg.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/rtl8812a/rtl8812a_mp.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/rtl8812a/usb/
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/rtl8812a/usb/usb_halinit.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/rtl8812a/usb/rtl8812au_xmit.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/rtl8812a/usb/rtl8812au_recv.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/rtl8812a/usb/rtl8812au_led.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/rtl8812a/usb/usb_ops_linux.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC-BTCoexist/
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC-BTCoexist/HalBtc8821a1Ant.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC-BTCoexist/HalBtc8192e1Ant.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC-BTCoexist/HalBtc8192e1Ant.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC-BTCoexist/HalBtc8192d2Ant.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC-BTCoexist/HalBtc8723b1Ant.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC-BTCoexist/Mp_Precomp.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC-BTCoexist/HalBtc8821a2Ant.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC-BTCoexist/HalBtc8812a2Ant.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC-BTCoexist/HalBtc8188c2Ant.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC-BTCoexist/HalBtc8821a2Ant.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC-BTCoexist/HalBtcOutSrc.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC-BTCoexist/HalBtc8812a1Ant.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC-BTCoexist/HalBtc8192d2Ant.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC-BTCoexist/HalBtc8723a2Ant.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC-BTCoexist/HalBtc8723a2Ant.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC-BTCoexist/HalBtc8723a1Ant.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC-BTCoexist/HalBtc8821a1Ant.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC-BTCoexist/HalBtc8723b2Ant.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC-BTCoexist/HalBtc8723b1Ant.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC-BTCoexist/HalBtc8812a1Ant.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC-BTCoexist/HalBtc8188c2Ant.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC-BTCoexist/HalBtc8723b2Ant.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC-BTCoexist/HalBtc8812a2Ant.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC-BTCoexist/HalBtc8192e2Ant.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC-BTCoexist/HalBtc8821aCsr2Ant.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC-BTCoexist/HalBtc8723a1Ant.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC-BTCoexist/HalBtc8821aCsr2Ant.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/OUTSRC-BTCoexist/HalBtc8192e2Ant.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/HalPwrSeqCmd.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/hal_btcoex.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/hal_com_phycfg.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/hal_com.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/hal_intf.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/hal/hal_phy.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/os_dep/
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/os_dep/linux/
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/os_dep/linux/wifi_regd.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/os_dep/linux/custom_gpio_linux.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/os_dep/linux/ioctl_linux.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/os_dep/linux/xmit_linux.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/os_dep/linux/mlme_linux.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/os_dep/linux/rtw_proc.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/os_dep/linux/os_intfs.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/os_dep/linux/ioctl_cfg80211.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/os_dep/linux/rtw_cfgvendor.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/os_dep/linux/recv_linux.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/os_dep/linux/usb_ops_linux.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/os_dep/linux/rtw_cfgvendor.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/os_dep/linux/rtw_android.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/os_dep/linux/rtw_proc.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/os_dep/linux/ioctl_cfg80211.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/os_dep/linux/usb_intf.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/os_dep/osdep_service.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/platform/
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/platform/platform_ARM_SUNxI_sdio.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/platform/platform_ARM_WMT_sdio.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/platform/platform_arm_act_sdio.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/platform/platform_ARM_SUNnI_sdio.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/platform/platform_sprd_sdio.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/platform/platform_ops.h
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/platform/platform_ARM_SUNxI_usb.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/platform/platform_RTK_DMP_usb.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/platform/platform_ops.c
rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51
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
cd platform ; rm -fr *.mod.c *.mod *.o .*.cmd *.ko
rm -fr Module.symvers ; rm -fr Module.markers ; rm -fr modules.order
rm -fr *.mod.c *.mod *.o .*.cmd *.ko *~
rm -fr .tmp_versions
Authentication requested [root] for make driver:
make ARCH=x86_64 CROSS_COMPILE= -C /lib/modules/4.4.0-83-generic/build 
M=/home/david/Downloads/Dongle/driver/rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51  modules
make[1]: Entering directory '/usr/src/linux-headers-4.4.0-83-generic'
  CC [M]  /home/david/Downloads/Dongle/driver/rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-
51/core/rtw_cmd.o
In file included from /home/david/Downloads/Dongle/driver/rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128
-51/include/drv_types.h:95:0,
                 from /home/david/Downloads/Dongle/driver/rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128
-51/core/rtw_cmd.c:22:
/home/david/Downloads/Dongle/driver/rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-
51/include/hal_com.h:412:13: error: ‘file_path’ redeclared as different kind of symbol
 extern char file_path[PATH_LENGTH_MAX];
             ^
In file included from include/linux/compat.h:15:0,
                 from include/linux/ethtool.h:16,
                 from include/linux/netdevice.h:42,
                 from /home/david/Downloads/Dongle/driver/rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128
-51/include/osdep_service_linux.h:35,
                 from /home/david/Downloads/Dongle/driver/rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128
-51/include/osdep_service.h:41,
                 from /home/david/Downloads/Dongle/driver/rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128
-51/include/drv_types.h:32,
                 from /home/david/Downloads/Dongle/driver/rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128
-51/core/rtw_cmd.c:22:
include/linux/fs.h:2605:14: note: previous declaration of ‘file_path’ was here
 extern char *file_path(struct file *, char *, int);
              ^
In file included from /home/david/Downloads/Dongle/driver/rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128
-51/include/drv_types.h:65:0,
                 from /home/david/Downloads/Dongle/driver/rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128
-51/core/rtw_cmd.c:22:
/home/david/Downloads/Dongle/driver/rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/core/rtw_cmd.c: In 
function ‘btinfo_evt_dump’:
/home/david/Downloads/Dongle/driver/rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-
51/include/rtw_debug.h:187:19: error: void value not ignored as it ought to be
  #define _seqdump seq_printf
                   ^
/home/david/Downloads/Dongle/driver/rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-
51/include/rtw_debug.h:242:7: note: in expansion of macro ‘_seqdump’
    if(_seqdump(sel, fmt, ##arg)) /*rtw_warn_on(1)*/; \
       ^
/home/david/Downloads/Dongle/driver/rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-
51/core/rtw_cmd.c:3293:2: note: in expansion of macro ‘DBG_871X_SEL_NL’
  DBG_871X_SEL_NL(sel, "cid:0x%02x, len:%u\n", info->cid, info->len);
  ^
/home/david/Downloads/Dongle/driver/rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-
51/include/rtw_debug.h:187:19: error: void value not ignored as it ought to be
  #define _seqdump seq_printf
                   ^
/home/david/Downloads/Dongle/driver/rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-
51/include/rtw_debug.h:242:7: note: in expansion of macro ‘_seqdump’
    if(_seqdump(sel, fmt, ##arg)) /*rtw_warn_on(1)*/; \
       ^
/home/david/Downloads/Dongle/driver/rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-
51/core/rtw_cmd.c:3296:3: note: in expansion of macro ‘DBG_871X_SEL_NL’
   DBG_871X_SEL_NL(sel, "byte2:%s%s%s%s%s%s%s%s\n"
   ^
/home/david/Downloads/Dongle/driver/rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-
51/include/rtw_debug.h:187:19: error: void value not ignored as it ought to be
  #define _seqdump seq_printf
                   ^
/home/david/Downloads/Dongle/driver/rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-
51/include/rtw_debug.h:242:7: note: in expansion of macro ‘_seqdump’
    if(_seqdump(sel, fmt, ##arg)) /*rtw_warn_on(1)*/; \
       ^
/home/david/Downloads/Dongle/driver/rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-
51/core/rtw_cmd.c:3308:3: note: in expansion of macro ‘DBG_871X_SEL_NL’
   DBG_871X_SEL_NL(sel, "retry_cnt:%u\n", info->retry_cnt);
   ^
/home/david/Downloads/Dongle/driver/rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-
51/include/rtw_debug.h:187:19: error: void value not ignored as it ought to be
  #define _seqdump seq_printf
                   ^
/home/david/Downloads/Dongle/driver/rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-
51/include/rtw_debug.h:242:7: note: in expansion of macro ‘_seqdump’
    if(_seqdump(sel, fmt, ##arg)) /*rtw_warn_on(1)*/; \
       ^
/home/david/Downloads/Dongle/driver/rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-
51/core/rtw_cmd.c:3311:3: note: in expansion of macro ‘DBG_871X_SEL_NL’
   DBG_871X_SEL_NL(sel, "rssi:%u\n", info->rssi);
   ^
/home/david/Downloads/Dongle/driver/rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-
51/include/rtw_debug.h:187:19: error: void value not ignored as it ought to be
  #define _seqdump seq_printf
                   ^
/home/david/Downloads/Dongle/driver/rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-
51/include/rtw_debug.h:242:7: note: in expansion of macro ‘_seqdump’
    if(_seqdump(sel, fmt, ##arg)) /*rtw_warn_on(1)*/; \
       ^
/home/david/Downloads/Dongle/driver/rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-
51/core/rtw_cmd.c:3314:3: note: in expansion of macro ‘DBG_871X_SEL_NL’
   DBG_871X_SEL_NL(sel, "byte5:%s%s\n"
   ^
scripts/Makefile.build:258: recipe for target 
'/home/david/Downloads/Dongle/driver/rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51/core/rtw_cmd.o' 
failed
make[2]: *** [/home/david/Downloads/Dongle/driver/rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-
51/core/rtw_cmd.o] Error 1
Makefile:1420: recipe for target 
'_module_/home/david/Downloads/Dongle/driver/rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128-51' failed
make[1]: *** [_module_/home/david/Downloads/Dongle/driver/rtl8821AU_linux_v4.3.14_13455.20150212_BTCOEX20150128
-51] Error 2
make[1]: Leaving directory '/usr/src/linux-headers-4.4.0-83-generic'
Makefile:1551: recipe for target 'modules' failed
make: *** [modules] Error 2
##################################################
Compile make driver error: 2
Please check error Mesg
##################################################


``` Any advice on how to proceed would be appreciated.

---

### Post by jet-bundle on 2017-08-11
A solution has been given in another thread, so I'll mark this as solved.

EDIT [https://ubuntuforums.org/showthread.php?t=2368422](https://ubuntuforums.org/showthread.php?t=2368422)

---

### Post by wildmanne39 on 2017-08-11
Please include a link to the solution so the whole community will benefit.

Thanks

---

