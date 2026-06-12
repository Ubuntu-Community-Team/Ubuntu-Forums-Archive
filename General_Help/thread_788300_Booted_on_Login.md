---
title: "Booted on Login"
date: 2008-05-09
forum: General Help
---

### Post by pootsey on 2008-05-09
Hey there guys,

Now I am not a complete noob with ubuntu - I used it a year or two back and decided to use it again on a permanent basis (well, providing I can eventually get logged in!).

Now, I did a fresh installation and it all went well but now when I login it hangs for a couple of seconds, then 2 black bands come across top and bottom of screen and then it boots me back to login screen.

Now the user+pass are fine because I can login via failsafe Gnome and use failsafe terminal so I can only assume this is a problem with gnome itself or my users permissions...if it helps I did try creating another user through failsafe gnome as admin but it still hangs then sends back to login.

Help! :(

---

### Post by prshah on 2008-05-09
> **pootsey said:**
> Hey there guys,
but now when I login it hangs for a couple of seconds, then 2 black bands come across top and bottom of screen and then it boots me back to login screen.

Now the user+pass are fine because I can login via failsafe Gnome and use failsafe terminal 

Please post the following files for clues:

/var/log/messages
/var/log/Xorg.0.log

---

### Post by pootsey on 2008-05-10
> **messages]May 10 15:15:15 thomas-desktop syslogd 1.5.0#1ubuntu1: restart.
May 10 15:15:18 thomas-desktop kernel: [  915.886266] wlan0: association FAILED: peer sent Status Code 12 (Assoc denied (reason outside of 802.11b scope) -- maybe MAC filtering by peer?)
May 10 15:15:19 thomas-desktop kernel: [  917.382434] wlan0: association FAILED: peer sent Status Code 12 (Assoc denied (reason outside of 802.11b scope) -- maybe MAC filtering by peer?)
May 10 15:15:22 thomas-desktop kernel: [  919.881215] wlan0: association FAILED: peer sent Status Code 12 (Assoc denied (reason outside of 802.11b scope) -- maybe MAC filtering by peer?)
May 10 15:15:24 thomas-desktop kernel: [  922.380478] wlan0: association FAILED: peer sent Status Code 12 (Assoc denied (reason outside of 802.11b scope) -- maybe MAC filtering by peer?)
May 10 15:15:27 thomas-desktop kernel: [  924.879726] wlan0: association FAILED: peer sent Status Code 12 (Assoc denied (reason outside of 802.11b scope) -- maybe MAC filtering by peer?)
May 10 15:15:29 thomas-desktop kernel: [  927.379001] wlan0: association FAILED: peer sent Status Code 12 (Assoc denied (reason outside of 802.11b scope) -- maybe MAC filtering by peer?)
May 10 15:15:32 thomas-desktop kernel: [  929.878249] wlan0: association FAILED: peer sent Status Code 12 (Assoc denied (reason outside of 802.11b scope) -- maybe MAC filtering by peer?)
May 10 15:15:34 thomas-desktop kernel: [  932.377514] wlan0: association FAILED: peer sent Status Code 12 (Assoc denied (reason outside of 802.11b scope) -- maybe MAC filtering by peer?)
May 10 15:15:37 thomas-desktop kernel: [  934.876776] wlan0: association FAILED: peer sent Status Code 12 (Assoc denied (reason outside of 802.11b scope) -- maybe MAC filtering by peer?)
May 10 15:15:39 thomas-desktop kernel: [  937.376026] wlan0: association FAILED: peer sent Status Code 12 (Assoc denied (reason outside of 802.11b scope) -- maybe MAC filtering by peer?)
May 10 15:15:44 thomas-desktop kernel: [  941.621761] wlan0: association FAILED: peer sent Status Code 12 (Assoc denied (reason outside of 802.11b scope) -- maybe MAC filtering by peer?)
May 10 15:15:45 thomas-desktop kernel: [  943.118316] wlan0: association FAILED: peer sent Status Code 12 (Assoc denied (reason outside of 802.11b scope) -- maybe MAC filtering by peer?)
May 10 15:15:48 thomas-desktop kernel: [  945.617587] wlan0: association FAILED: peer sent Status Code 12 (Assoc denied (reason outside of 802.11b scope) -- maybe MAC filtering by peer?)
May 10 15:15:50 thomas-desktop kernel: [  948.116839] wlan0: association FAILED: peer sent Status Code 12 (Assoc denied (reason outside of 802.11b scope) -- maybe MAC filtering by peer?)
May 10 15:15:53 thomas-desktop kernel: [  950.616112] wlan0: association FAILED: peer sent Status Code 12 (Assoc denied (reason outside of 802.11b scope) -- maybe MAC filtering by peer?)
May 10 15:15:55 thomas-desktop kernel: [  953.115354] wlan0: association FAILED: peer sent Status Code 12 (Assoc denied (reason outside of 802.11b scope) -- maybe MAC filtering by peer?)
May 10 15:15:58 thomas-desktop kernel: [  955.614618] wlan0: association FAILED: peer sent Status Code 12 (Assoc denied (reason outside of 802.11b scope) -- maybe MAC filtering by peer?)
May 10 15:16:00 thomas-desktop kernel: [  958.113884] wlan0: association FAILED: peer sent Status Code 12 (Assoc denied (reason outside of 802.11b scope) -- maybe MAC filtering by peer?)
May 10 15:16:03 thomas-desktop kernel: [  960.613139] wlan0: association FAILED: peer sent Status Code 12 (Assoc denied (reason outside of 802.11b scope) -- maybe MAC filtering by peer?)
May 10 15:16:05 thomas-desktop kernel: [  963.112398] wlan0: association FAILED: peer sent Status Code 12 (Assoc denied (reason outside of 802.11b scope) -- maybe MAC filtering by peer?)
May 10 15:16:10 thomas-desktop kernel: [  967.664981] wlan0: association FAILED: peer sent Status Code 12 (Assoc denied (reason outside of 802.11b scope) -- maybe MAC filtering by peer?)
May 10 15:16:11 thomas-desktop kernel: [  969.162600] wlan0: association FAILED: peer sent Status Code 12 (Assoc denied (reason outside of 802.11b scope) -- maybe MAC filtering by peer?)
May 10 15:16:14 thomas-desktop kernel: [  971.661858] wlan0: association FAILED: peer sent Status Code 12 (Assoc denied (reason outside of 802.11b scope) -- maybe MAC filtering by peer?)
May 10 15:16:16 thomas-desktop kernel: [  974.161117] wlan0: association FAILED: peer sent Status Code 12 (Assoc denied (reason outside of 802.11b scope) -- maybe MAC filtering by peer?)
May 10 15:16:19 thomas-desktop kernel: [  976.660208] wlan0: association FAILED: peer sent Status Code 12 (Assoc denied (reason outside of 802.11b scope) -- maybe MAC filtering by peer?)
May 10 15:16:21 thomas-desktop kernel: [  979.159474] wlan0: association FAILED: peer sent Status Code 12 (Assoc denied (reason outside of 802.11b scope) -- maybe MAC filtering by peer?)
May 10 15:16:24 thomas-desktop kernel: [  981.658735] wlan0: association FAILED: peer sent Status Code 12 (Assoc denied (reason outside of 802.11b scope) -- maybe MAC filtering by peer?)
May 10 15:16:26 thomas-desktop kernel: [  984.157989] wlan0: association FAILED: peer sent Status Code 12 (Assoc denied (reason outside of 802.11b scope) -- maybe MAC filtering by peer?)
May 10 15:16:29 thomas-desktop kernel: [  986.657246] wlan0: association FAILED: peer sent Status Code 12 (Assoc denied (reason outside of 802.11b scope) -- maybe MAC filtering by peer?)
May 10 15:16:31 thomas-desktop kernel: [  989.156508] wlan0: association FAILED: peer sent Status Code 12 (Assoc denied (reason outside of 802.11b scope) -- maybe MAC filtering by peer?)
May 10 15:16:36 thomas-desktop kernel: [  993.607502] wlan0: association FAILED: peer sent Status Code 12 (Assoc denied (reason outside of 802.11b scope) -- maybe MAC filtering by peer?)
May 10 15:16:37 thomas-desktop kernel: [  995.102914] wlan0: association FAILED: peer sent Status Code 12 (Assoc denied (reason outside of 802.11b scope) -- maybe MAC filtering by peer?)
May 10 15:16:40 thomas-desktop kernel: [  997.602169] wlan0: association FAILED: peer sent Status Code 12 (Assoc denied (reason outside of 802.11b scope) -- maybe MAC filtering by peer?)
May 10 15:16:42 thomas-desktop kernel: [ 1000.101432] wlan0: association FAILED: peer sent Status Code 12 (Assoc denied (reason outside of 802.11b scope) -- maybe MAC filtering by peer?)
May 10 15:16:45 thomas-desktop kernel: [ 1002.600684] wlan0: association FAILED: peer sent Status Code 12 (Assoc denied (reason outside of 802.11b scope) -- maybe MAC filtering by peer?)
May 10 15:16:47 thomas-desktop kernel: [ 1005.099950] wlan0: association FAILED: peer sent Status Code 12 (Assoc denied (reason outside of 802.11b scope) -- maybe MAC filtering by peer?)
May 10 15:16:51 thomas-desktop kernel: [ 1009.141954] wlan0: association FAILED: peer sent Status Code 12 (Assoc denied (reason outside of 802.11b scope) -- maybe MAC filtering by peer?)
May 10 15:16:52 thomas-desktop kernel: [ 1010.098463] wlan0: association FAILED: peer sent Status Code 12 (Assoc denied (reason outside of 802.11b scope) -- maybe MAC filtering by peer?)
May 10 15:16:55 thomas-desktop kernel: [ 1012.597724] wlan0: association FAILED: peer sent Status Code 12 (Assoc denied (reason outside of 802.11b scope) -- maybe MAC filtering by peer?)
May 10 15:16:57 thomas-desktop kernel: [ 1015.096971] wlan0: association FAILED: peer sent Status Code 12 (Assoc denied (reason outside of 802.11b scope) -- maybe MAC filtering by peer?)
May 10 15:17:02 thomas-desktop kernel: [ 1019.649581] wlan0: association FAILED: peer sent Status Code 12 (Assoc denied (reason outside of 802.11b scope) -- maybe MAC filtering by peer?)
May 10 15:17:03 thomas-desktop kernel: [ 1021.147184] wlan0: association FAILED: peer sent Status Code 12 (Assoc denied (reason outside of 802.11b scope) -- maybe MAC filtering by peer?)
May 10 15:17:06 thomas-desktop kernel: [ 1023.646286] wlan0: association FAILED: peer sent Status Code 12 (Assoc denied (reason outside of 802.11b scope) -- maybe MAC filtering by peer?)
May 10 15:17:08 thomas-desktop kernel: [ 1026.145558] wlan0: association FAILED: peer sent Status Code 12 (Assoc denied (reason outside of 802.11b scope) -- maybe MAC filtering by peer?)
May 10 15:17:11 thomas-desktop kernel: [ 1028.644818] wlan0: association FAILED: peer sent Status Code 12 (Assoc denied (reason outside of 802.11b scope) -- maybe MAC filtering by peer?)
May 10 15:17:13 thomas-desktop kernel: [ 1031.144068] wlan0: association FAILED: peer sent Status Code 12 (Assoc denied (reason outside of 802.11b scope) -- maybe MAC filtering by peer?)
May 10 15:17:16 thomas-desktop kernel: [ 1033.643327] wlan0: association FAILED: peer sent Status Code 12 (Assoc denied (reason outside of 802.11b scope) -- maybe MAC filtering by peer?)
May 10 15:17:18 thomas-desktop kernel: [ 1036.142580] wlan0: association FAILED: peer sent Status Code 12 (Assoc denied (reason outside of 802.11b scope) -- maybe MAC filtering by peer?)
May 10 15:17:21 thomas-desktop kernel: [ 1038.641844] wlan0: association FAILED: peer sent Status Code 12 (Assoc denied (reason outside of 802.11b scope) -- maybe MAC filtering by peer?)
May 10 15:17:23 thomas-desktop kernel: [ 1041.141102] wlan0: association FAILED: peer sent Status Code 12 (Assoc denied (reason outside of 802.11b scope) -- maybe MAC filtering by peer?)
May 10 15:17:28 thomas-desktop kernel: [ 1045.898732] wlan0: association FAILED: peer sent Status Code 12 (Assoc denied (reason outside of 802.11b scope) -- maybe MAC filtering by peer?)
May 10 15:17:30 thomas-desktop kernel: [ 1047.395412] wlan0: association FAILED: peer sent Status Code 12 (Assoc denied (reason outside of 802.11b scope) -- maybe MAC filtering by peer?)
May 10 15:17:32 thomas-desktop kernel: [ 1049.895189] wlan0: association FAILED: peer sent Status Code 12 (Assoc denied (reason outside of 802.11b scope) -- maybe MAC filtering by peer?)
May 10 15:17:35 thomas-desktop kernel: [ 1052.393938] wlan0: association FAILED: peer sent Status Code 12 (Assoc denied (reason outside of 802.11b scope) -- maybe MAC filtering by peer?)
May 10 15:17:37 thomas-desktop kernel: [ 1054.893635] wlan0: association FAILED: peer sent Status Code 12 (Assoc denied (reason outside of 802.11b scope) -- maybe MAC filtering by peer?)
May 10 15:17:40 thomas-desktop kernel: [ 1057.392455] wlan0: association FAILED: peer sent Status Code 12 (Assoc denied (reason outside of 802.11b scope) -- maybe MAC filtering by peer?)
May 10 15:17:42 thomas-desktop kernel: [ 1059.891720] wlan0: association FAILED: peer sent Status Code 12 (Assoc denied (reason outside of 802.11b scope) -- maybe MAC filtering by peer?)
May 10 15:17:45 thomas-desktop kernel: [ 1062.390969] wlan0: association FAILED: peer sent Status Code 12 (Assoc denied (reason outside of 802.11b scope) -- maybe MAC filtering by peer?)
May 10 15:17:47 thomas-desktop kernel: [ 1064.890225] wlan0: association FAILED: peer sent Status Code 12 (Assoc denied (reason outside of 802.11b scope) -- maybe MAC filtering by peer?)
May 10 15:17:50 thomas-desktop kernel: [ 1067.389492] wlan0: association FAILED: peer sent Status Code 12 (Assoc denied (reason outside of 802.11b scope) -- maybe MAC filtering by peer?)
May 10 15:17:54 thomas-desktop kernel: [ 1071.942892] wlan0: association FAILED: peer sent Status Code 12 (Assoc denied (reason outside of 802.11b scope) -- maybe MAC filtering by peer?)
May 10 15:17:56 thomas-desktop kernel: [ 1073.439531] wlan0: association FAILED: peer sent Status Code 12 (Assoc denied (reason outside of 802.11b scope) -- maybe MAC filtering by peer?)
May 10 15:17:58 thomas-desktop kernel: [ 1075.938788] wlan0: association FAILED: peer sent Status Code 12 (Assoc denied (reason outside of 802.11b scope) -- maybe MAC filtering by peer?)
May 10 15:18:01 thomas-desktop kernel: [ 1078.438049] wlan0: association FAILED: peer sent Status Code 12 (Assoc denied (reason outside of 802.11b scope) -- maybe MAC filtering by peer?)
May 10 15:18:03 thomas-desktop kernel: [ 1080.937311] wlan0: association FAILED: peer sent Status Code 12 (Assoc denied (reason outside of 802.11b scope) -- maybe MAC filtering by peer?)
May 10 15:18:06 thomas-desktop kernel: [ 1083.436564] wlan0: association FAILED: peer sent Status Code 12 (Assoc denied (reason outside of 802.11b scope) -- maybe MAC filtering by peer?)
May 10 15:18:08 thomas-desktop kernel: [ 1085.935826] wlan0: association FAILED: peer sent Status Code 12 (Assoc denied (reason outside of 802.11b scope) -- maybe MAC filtering by peer?)
May 10 15:18:11 thomas-desktop kernel: [ 1088.435087] wlan0: association FAILED: peer sent Status Code 12 (Assoc denied (reason outside of 802.11b scope) -- maybe MAC filtering by peer?)
May 10 15:18:13 thomas-desktop kernel: [ 1090.934352] wlan0: association FAILED: peer sent Status Code 12 (Assoc denied (reason outside of 802.11b scope) -- maybe MAC filtering by peer?)
May 10 15:18:16 thomas-desktop kernel: [ 1093.433603] wlan0: association FAILED: peer sent Status Code 12 (Assoc denied (reason outside of 802.11b scope) -- maybe MAC filtering by peer?)
May 10 15:18:20 thomas-desktop kernel: [ 1098.293402] wlan0: association FAILED: peer sent Status Code 12 (Assoc denied (reason outside of 802.11b scope) -- maybe MAC filtering by peer?)
May 10 15:18:22 thomas-desktop kernel: [ 1099.791891] wlan0: association FAILED: peer sent Status Code 12 (Assoc denied (reason outside of 802.11b scope) -- maybe MAC filtering by peer?)
May 10 15:18:24 thomas-desktop kernel: [ 1102.291154] wlan0: association FAILED: peer sent Status Code 12 (Assoc denied (reason outside of 802.11b scope) -- maybe MAC filtering by peer?)
May 10 15:18:27 thomas-desktop kernel: [ 1104.790406] wlan0: association FAILED: peer sent Status Code 12 (Assoc denied (reason outside of 802.11b scope) -- maybe MAC filtering by peer?)
May 10 15:18:29 thomas-desktop kernel: [ 1107.289660] wlan0: association FAILED: peer sent Status Code 12 (Assoc denied (reason outside of 802.11b scope) -- maybe MAC filtering by peer?)
May 10 15:18:32 thomas-desktop kernel: [ 1109.788921] wlan0: association FAILED: peer sent Status Code 12 (Assoc denied (reason outside of 802.11b scope) -- maybe MAC filtering by peer?)
May 10 15:18:34 thomas-desktop kernel: [ 1112.288180] wlan0: association FAILED: peer sent Status Code 12 (Assoc denied (reason outside of 802.11b scope) -- maybe MAC filtering by peer?)
May 10 15:18:37 thomas-desktop kernel: [ 1114.787448] wlan0: association FAILED: peer sent Status Code 12 (Assoc denied (reason outside of 802.11b scope) -- maybe MAC filtering by peer?)
May 10 15:18:39 thomas-desktop kernel: [ 1117.286704] wlan0: association FAILED: peer sent Status Code 12 (Assoc denied (reason outside of 802.11b scope) -- maybe MAC filtering by peer?)
May 10 15:18:42 thomas-desktop kernel: [ 1119.785802] wlan0: association FAILED: peer sent Status Code 12 (Assoc denied (reason outside of 802.11b scope) -- maybe MAC filtering by peer?)
May 10 15:18:47 thomas-desktop kernel: [ 1124.543798] wlan0: association FAILED: peer sent Status Code 12 (Assoc denied (reason outside of 802.11b scope) -- maybe MAC filtering by peer?)
May 10 15:18:48 thomas-desktop kernel: [ 1126.040111] wlan0: association FAILED: peer sent Status Code 12 (Assoc denied (reason outside of 802.11b scope) -- maybe MAC filtering by peer?)
May 10 15:18:51 thomas-desktop kernel: [ 1128.539393] wlan0: association FAILED: peer sent Status Code 12 (Assoc denied (reason outside of 802.11b scope) -- maybe MAC filtering by peer?)
May 10 15:18:53 thomas-desktop kernel: [ 1131.038645] wlan0: association FAILED: peer sent Status Code 12 (Assoc denied (reason outside of 802.11b scope) -- maybe MAC filtering by peer?)
May 10 15:18:56 thomas-desktop kernel: [ 1133.537902] wlan0: association FAILED: peer sent Status Code 12 (Assoc denied (reason outside of 802.11b scope) -- maybe MAC filtering by peer?)
May 10 15:18:58 thomas-desktop kernel: [ 1136.037146] wlan0: association FAILED: peer sent Status Code 12 (Assoc denied (reason outside of 802.11b scope) -- maybe MAC filtering by peer?)
May 10 15:19:01 thomas-desktop kernel: [ 1139.029052] wlan0: association FAILED: peer sent Status Code 12 (Assoc denied (reason outside of 802.11b scope) -- maybe MAC filtering by peer?)
May 10 15:19:03 thomas-desktop kernel: [ 1141.035653] wlan0: association FAILED: peer sent Status Code 12 (Assoc denied (reason outside of 802.11b scope) -- maybe MAC filtering by peer?)
May 10 15:19:06 thomas-desktop kernel: [ 1143.535460] wlan0: association FAILED: peer sent Status Code 12 (Assoc denied (reason outside of 802.11b scope) -- maybe MAC filtering by peer?)
May 10 15:19:08 thomas-desktop kernel: [ 1146.034172] wlan0: association FAILED: peer sent Status Code 12 (Assoc denied (reason outside of 802.11b scope) -- maybe MAC filtering by peer?)
May 10 15:19:13 thomas-desktop kernel: [ 1150.791532] wlan0: association FAILED: peer sent Status Code 12 (Assoc denied (reason outside of 802.11b scope) -- maybe MAC filtering by peer?)
May 10 15:19:14 thomas-desktop kernel: [ 1152.288335] wlan0: association FAILED: peer sent Status Code 12 (Assoc denied (reason outside of 802.11b scope) -- maybe MAC filtering by peer?)
May 10 15:19:17 thomas-desktop kernel: [ 1154.787573] wlan0: association FAILED: peer sent Status Code 12 (Assoc denied (reason outside of 802.11b scope) -- maybe MAC filtering by peer?)
May 10 15:19:19 thomas-desktop kernel: [ 1157.286682] wlan0: association FAILED: peer sent Status Code 12 (Assoc denied (reason outside of 802.11b scope) -- maybe MAC filtering by peer?)
May 10 15:19:22 thomas-desktop kernel: [ 1159.785950] wlan0: association FAILED: peer sent Status Code 12 (Assoc denied (reason outside of 802.11b scope) -- maybe MAC filtering by peer?)
May 10 15:19:24 thomas-desktop kernel: [ 1162.286622] wlan0: association FAILED: peer sent Status Code 12 (Assoc denied (reason outside of 802.11b scope) -- maybe MAC filtering by peer?)
May 10 15:19:27 thomas-desktop kernel: [ 1164.784460] wlan0: association FAILED: peer sent Status Code 12 (Assoc denied (reason outside of 802.11b scope) -- maybe MAC filtering by peer?)
May 10 15:19:29 thomas-desktop kernel: [ 1167.283723] wlan0: association FAILED: peer sent Status Code 12 (Assoc denied (reason outside of 802.11b scope) -- maybe MAC filtering by peer?)
May 10 15:19:32 thomas-desktop kernel: [ 1169.783583] wlan0: association FAILED: peer sent Status Code 12 (Assoc denied (reason outside of 802.11b scope) -- maybe MAC filtering by peer?)
May 10 15:19:34 thomas-desktop kernel: [ 1172.282230] wlan0: association FAILED: peer sent Status Code 12 (Assoc denied (reason outside of 802.11b scope) -- maybe MAC filtering by peer?)
May 10 15:19:39 thomas-desktop kernel: [ 1177.142548] wlan0: association FAILED: peer sent Status Code 12 (Assoc denied (reason outside of 802.11b scope) -- maybe MAC filtering by peer?)
May 10 15:19:41 thomas-desktop kernel: [ 1178.640511] wlan0: association FAILED: peer sent Status Code 12 (Assoc denied (reason outside of 802.11b scope) -- maybe MAC filtering by peer?)
May 10 15:19:43 thomas-desktop kernel: [ 1181.139773] wlan0: association FAILED: peer sent Status Code 12 (Assoc denied (reason outside of 802.11b scope) -- maybe MAC filtering by peer?)
May 10 15:19:46 thomas-desktop kernel: [ 1183.639028] wlan0: association FAILED: peer sent Status Code 12 (Assoc denied (reason outside of 802.11b scope) -- maybe MAC filtering by peer?)
May 10 15:19:48 thomas-desktop kernel: [ 1186.138294] wlan0: association FAILED: peer sent Status Code 12 (Assoc denied (reason outside of 802.11b scope) -- maybe MAC filtering by peer?)
May 10 15:19:51 thomas-desktop kernel: [ 1188.637558] wlan0: association FAILED: peer sent Status Code 12 (Assoc denied (reason outside of 802.11b scope) -- maybe MAC filtering by peer?)
May 10 15:19:53 thomas-desktop kernel: [ 1191.136818] wlan0: association FAILED: peer sent Status Code 12 (Assoc denied (reason outside of 802.11b scope) -- maybe MAC filtering by peer?)
May 10 15:19:56 thomas-desktop kernel: [ 1193.636073] wlan0: association FAILED: peer sent Status Code 12 (Assoc denied (reason outside of 802.11b scope) -- maybe MAC filtering by peer?)
May 10 15:19:58 thomas-desktop kernel: [ 1196.135326] wlan0: association FAILED: peer sent Status Code 12 (Assoc denied (reason outside of 802.11b scope) -- maybe MAC filtering by peer?)
May 10 15:20:01 thomas-desktop kernel: [ 1198.635866] wlan0: association FAILED: peer sent Status Code 12 (Assoc denied (reason outside of 802.11b scope) -- maybe MAC filtering by peer?)
May 10 15:20:05 thomas-desktop kernel: [ 1203.289777] wlan0: association FAILED: peer sent Status Code 12 (Assoc denied (reason outside of 802.11b scope) -- maybe MAC filtering by peer?)
May 10 15:20:07 thomas-desktop kernel: [ 1204.788599] wlan0: association FAILED: peer sent Status Code 12 (Assoc denied (reason outside of 802.11b scope) -- maybe MAC filtering by peer?)
May 10 15:20:09 thomas-desktop kernel: [ 1207.287849] wlan0: association FAILED: peer sent Status Code 12 (Assoc denied (reason outside of 802.11b scope) -- maybe MAC filtering by peer?)
May 10 15:20:12 thomas-desktop kernel: [ 1209.787134] wlan0: association FAILED: peer sent Status Code 12 (Assoc denied (reason outside of 802.11b scope) -- maybe MAC filtering by peer?)
May 10 15:20:14 thomas-desktop kernel: [ 1212.286377] wlan0: association FAILED: peer sent Status Code 12 (Assoc denied (reason outside of 802.11b scope) -- maybe MAC filtering by peer?)
May 10 15:20:17 thomas-desktop kernel: [ 1214.785635] wlan0: association FAILED: peer sent Status Code 12 (Assoc denied (reason outside of 802.11b scope) -- maybe MAC filtering by peer?)
May 10 15:20:19 thomas-desktop kernel: [ 1217.284903] wlan0: association FAILED: peer sent Status Code 12 (Assoc denied (reason outside of 802.11b scope) -- maybe MAC filtering by peer?)
May 10 15:20:22 thomas-desktop kernel: [ 1219.784160] wlan0: association FAILED: peer sent Status Code 12 (Assoc denied (reason outside of 802.11b scope) -- maybe MAC filtering by peer?)
May 10 15:20:24 thomas-desktop kernel: [ 1222.283416] wlan0: association FAILED: peer sent Status Code 12 (Assoc denied (reason outside of 802.11b scope) -- maybe MAC filtering by peer?)
May 10 15:20:27 thomas-desktop kernel: [ 1224.783205] wlan0: association FAILED: peer sent Status Code 12 (Assoc denied (reason outside of 802.11b scope) -- maybe MAC filtering by peer?)
May 10 15:20:32 thomas-desktop kernel: [ 1229.440636] wlan0: association FAILED: peer sent Status Code 12 (Assoc denied (reason outside of 802.11b scope) -- maybe MAC filtering by peer?)
May 10 15:20:33 thomas-desktop kernel: [ 1230.937017] wlan0: association FAILED: peer sent Status Code 12 (Assoc denied (reason outside of 802.11b scope) -- maybe MAC filtering by peer?)
May 10 15:20:36 thomas-desktop kernel: [ 1233.436265] wlan0: association FAILED: peer sent Status Code 12 (Assoc denied (reason outside of 802.11b scope) -- maybe MAC filtering by peer?)
May 10 15:20:38 thomas-desktop kernel: [ 1235.935528] wlan0: association FAILED: peer sent Status Code 12 (Assoc denied (reason outside of 802.11b scope) -- maybe MAC filtering by peer?)
May 10 15:20:41 thomas-desktop kernel: [ 1238.434796] wlan0: association FAILED: peer sent Status Code 12 (Assoc denied (reason outside of 802.11b scope) -- maybe MAC filtering by peer?)
May 10 15:20:43 thomas-desktop kernel: [ 1240.934064] wlan0: association FAILED: peer sent Status Code 12 (Assoc denied (reason outside of 802.11b scope) -- maybe MAC filtering by peer?)
May 10 15:20:46 thomas-desktop kernel: [ 1243.433300] wlan0: association FAILED: peer sent Status Code 12 (Assoc denied (reason outside of 802.11b scope) -- maybe MAC filtering by peer?)
May 10 15:20:48 thomas-desktop kernel: [ 1245.932565] wlan0: association FAILED: peer sent Status Code 12 (Assoc denied (reason outside of 802.11b scope) -- maybe MAC filtering by peer?)
May 10 15:20:51 thomas-desktop kernel: [ 1248.431832] wlan0: association FAILED: peer sent Status Code 12 (Assoc denied (reason outside of 802.11b scope) -- maybe MAC filtering by peer?)
May 10 15:20:53 thomas-desktop kernel: [ 1250.931094] wlan0: association FAILED: peer sent Status Code 12 (Assoc denied (reason outside of 802.11b scope) -- maybe MAC filtering by peer?)
May 10 15:20:58 thomas-desktop kernel: [ 1255.688420] wlan0: association FAILED: peer sent Status Code 12 (Assoc denied (reason outside of 802.11b scope) -- maybe MAC filtering by peer?)
May 10 15:20:59 thomas-desktop kernel: [ 1257.185232] wlan0: association FAILED: peer sent Status Code 12 (Assoc denied (reason outside of 802.11b scope) -- maybe MAC filtering by peer?)
May 10 15:21:03 thomas-desktop kernel: [ 1259.684491] wlan0: association FAILED: peer sent Status Code 12 (Assoc denied (reason outside of 802.11b scope) -- maybe MAC filtering by peer?)
May 10 15:21:04 thomas-desktop kernel: [ 1262.183774] wlan0: association FAILED: peer sent Status Code 12 (Assoc denied (reason outside of 802.11b scope) -- maybe MAC filtering by peer?)
May 10 15:21:07 thomas-desktop kernel: [ 1264.683023] wlan0: association FAILED: peer sent Status Code 12 (Assoc denied (reason outside of 802.11b scope) -- maybe MAC filtering by peer?)
May 10 15:21:11 thomas-desktop kernel: [ 1268.813761] wlan0: association FAILED: peer sent Status Code 12 (Assoc denied (reason outside of 802.11b scope) -- maybe MAC filtering by peer?)
May 10 15:21:12 thomas-desktop kernel: [ 1269.681535] wlan0: association FAILED: peer sent Status Code 12 (Assoc denied (reason outside of 802.11b scope) -- maybe MAC filtering by peer?)
May 10 15:21:14 thomas-desktop kernel: [ 1272.180808] wlan0: association FAILED: peer sent Status Code 12 (Assoc denied (reason outside of 802.11b scope) -- maybe MAC filtering by peer?)
May 10 15:21:17 thomas-desktop kernel: [ 1274.680052] wlan0: association FAILED: peer sent Status Code 12 (Assoc denied (reason outside of 802.11b scope) -- maybe MAC filtering by peer?)
May 10 15:21:18 thomas-desktop kernel: [ 1275.456493] NET: Registered protocol family 10
May 10 15:21:18 thomas-desktop kernel: [ 1275.457673] lo: Disabled Privacy Extensions
May 10 15:21:18 thomas-desktop kernel: [ 1275.459163] ADDRCONF(NETDEV_UP): eth0: link is not ready
May 10 15:21:18 thomas-desktop kernel: [ 1275.460342] ADDRCONF(NETDEV_UP): wlan0: link is not ready
May 10 15:21:19 thomas-desktop kernel: [ 1277.179342] wlan0: association FAILED: peer sent Status Code 12 (Assoc denied (reason outside of 802.11b scope) -- maybe MAC filtering by peer?)
May 10 15:21:24 thomas-desktop kernel: [ 1281.936646] wlan0: association FAILED: peer sent Status Code 12 (Assoc denied (reason outside of 802.11b scope) -- maybe MAC filtering by peer?)
May 10 15:21:26 thomas-desktop kernel: [ 1283.433476] wlan0: association FAILED: peer sent Status Code 12 (Assoc denied (reason outside of 802.11b scope) -- maybe MAC filtering by peer?)
May 10 15:21:28 thomas-desktop kernel: [ 1285.932729] wlan0: association FAILED: peer sent Status Code 12 (Assoc denied (reason outside of 802.11b scope) -- maybe MAC filtering by peer?)
May 10 15:21:31 thomas-desktop kernel: [ 1288.431968] wlan0: association FAILED: peer sent Status Code 12 (Assoc denied (reason outside of 802.11b scope) -- maybe MAC filtering by peer?)
May 10 15:21:33 thomas-desktop kernel: [ 1290.931780] wlan0: association FAILED: peer sent Status Code 12 (Assoc denied (reason outside of 802.11b scope) -- maybe MAC filtering by peer?)
May 10 15:21:36 thomas-desktop kernel: [ 1293.430483] wlan0: association FAILED: peer sent Status Code 12 (Assoc denied (reason outside of 802.11b scope) -- maybe MAC filtering by peer?)
May 10 15:21:38 thomas-desktop kernel: [ 1295.929755] wlan0: association FAILED: peer sent Status Code 12 (Assoc denied (reason outside of 802.11b scope) -- maybe MAC filtering by peer?)
May 10 15:21:41 thomas-desktop kernel: [ 1298.429011] wlan0: association FAILED: peer sent Status Code 12 (Assoc denied (reason outside of 802.11b scope) -- maybe MAC filtering by peer?)
May 10 15:21:43 thomas-desktop kernel: [ 1301.911393] wlan0: association FAILED: peer sent Status Code 12 (Assoc denied (reason outside of 802.11b scope) -- maybe MAC filtering by peer?)
May 10 15:21:46 thomas-desktop kernel: [  724.922225] wlan0: association FAILED: peer sent Status Code 12 (Assoc denied (reason outside of 802.11b scope) -- maybe MAC filtering by peer?)
May 10 15:21:50 thomas-desktop kernel: [  728.918524] wlan0: association FAILED: peer sent Status Code 12 (Assoc denied (reason outside of 802.11b scope) -- maybe MAC filtering by peer?)
May 10 15:21:52 thomas-desktop kernel: [  730.414119] wlan0: association FAILED: peer sent Status Code 12 (Assoc denied (reason outside of 802.11b scope) -- maybe MAC filtering by peer?)
May 10 15:21:54 thomas-desktop kernel: [  732.910462] wlan0: association FAILED: peer sent Status Code 12 (Assoc denied (reason outside of 802.11b scope) -- maybe MAC filtering by peer?)
May 10 15:21:57 thomas-desktop kernel: [  735.406809] wlan0: association FAILED: peer sent Status Code 12 (Assoc denied (reason outside of 802.11b scope) -- maybe MAC filtering by peer?)
May 10 15:21:59 thomas-desktop kernel: [  737.903150] wlan0: association FAILED: peer sent Status Code 12 (Assoc denied (reason outside of 802.11b scope) -- maybe MAC filtering by peer?)
May 10 15:22:02 thomas-desktop kernel: [ 1332.354536] wlan0: association FAILED: peer sent Status Code 12 (Assoc denied (reason outside of 802.11b scope) -- maybe MAC filtering by peer?)
May 10 15:22:03 thomas-desktop kernel: [  740.752630] [drm] Setting GART location based on new memory map
May 10 15:22:03 thomas-desktop kernel: [  740.753096] [drm] Loading R300 Microcode
May 10 15:22:03 thomas-desktop kernel: [  740.753117] [drm] writeback test succeeded in 1 usecs
May 10 15:22:04 thomas-desktop kernel: [  741.794106] wlan0: association FAILED: peer sent Status Code 12 (Assoc denied (reason outside of 802.11b scope) -- maybe MAC filtering by peer?)
May 10 15:22:07 thomas-desktop kernel: [ 1339.334435] wlan0: association FAILED: peer sent Status Code 12 (Assoc denied (reason outside of 802.11b scope) -- maybe MAC filtering by peer?)
May 10 15:22:09 thomas-desktop kernel: [ 1341.833698] wlan0: association FAILED: peer sent Status Code 12 (Assoc denied (reason outside of 802.11b scope) -- maybe MAC filtering by peer?)
May 10 15:22:12 thomas-desktop kernel: [  747.080802] wlan0: association FAILED: peer sent Status Code 12 (Assoc denied (reason outside of 802.11b scope) -- maybe MAC filtering by peer?)
May 10 15:22:16 thomas-desktop kernel: [ 1352.953117] wlan0: association FAILED: peer sent Status Code 12 (Assoc denied (reason outside of 802.11b scope) -- maybe MAC filtering by peer?)
May 10 15:22:18 thomas-desktop kernel: [ 1354.451977] wlan0: association FAILED: peer sent Status Code 12 (Assoc denied (reason outside of 802.11b scope) -- maybe MAC filtering by peer?)
May 10 15:22:20 thomas-desktop kernel: [ 1356.951206] wlan0: association FAILED: peer sent Status Code 12 (Assoc denied (reason outside of 802.11b scope) -- maybe MAC filtering by peer?)
May 10 15:22:23 thomas-desktop kernel: [ 1359.450506] wlan0: association FAILED: peer sent Status Code 12 (Assoc denied (reason outside of 802.11b scope) -- maybe MAC filtering by peer?)
May 10 15:22:25 thomas-desktop kernel: [ 1361.949759] wlan0: association FAILED: peer sent Status Code 12 (Assoc denied (reason outside of 802.11b scope) -- maybe MAC filtering by peer?)
May 10 15:22:28 thomas-desktop kernel: [ 1365.436079] wlan0: association FAILED: peer sent Status Code 12 (Assoc denied (reason outside of 802.11b scope) -- maybe MAC filtering by peer?)
May 10 15:22:30 thomas-desktop kernel: [  759.101691] wlan0: association FAILED: peer sent Status Code 12 (Assoc denied (reason outside of 802.11b scope) -- maybe MAC filtering by peer?)
May 10 15:22:33 thomas-desktop kernel: [  761.598056] wlan0: association FAILED: peer sent Status Code 12 (Assoc denied (reason outside of 802.11b scope) -- maybe MAC filtering by peer?)
May 10 15:22:34 thomas-desktop pulseaudio[12620]: pid.c: Stale PID file, overwriting.
May 10 15:22:35 thomas-desktop kernel: [  764.094403] wlan0: association FAILED: peer sent Status Code 12 (Assoc denied (reason outside of 802.11b scope) -- maybe MAC filtering by peer?)
May 10 15:22:38 thomas-desktop kernel: [  766.590730] wlan0: association FAILED: peer sent Status Code 12 (Assoc denied (reason outside of 802.11b scope) -- maybe MAC filtering by peer?)
May 10 15:22:42 thomas-desktop kernel: [  770.933860] wlan0: association FAILED: peer sent Status Code 12 (Assoc denied (reason outside of 802.11b scope) -- maybe MAC filtering by peer?)
May 10 15:22:44 thomas-desktop kernel: [ 1391.209883] wlan0: association FAILED: peer sent Status Code 12 (Assoc denied (reason outside of 802.11b scope) -- maybe MAC filtering by peer?)
May 10 15:22:46 thomas-desktop kernel: [  773.831088] wlan0: association FAILED: peer sent Status Code 12 (Assoc denied (reason outside of 802.11b scope) -- maybe MAC filtering by peer?)
May 10 15:22:49 thomas-desktop kernel: [  776.327439] wlan0: association FAILED: peer sent Status Code 12 (Assoc denied (reason outside of 802.11b scope) -- maybe MAC filtering by peer?)
May 10 15:22:51 thomas-desktop kernel: [  778.825170] wlan0: association FAILED: peer sent Status Code 12 (Assoc denied (reason outside of 802.11b scope) -- maybe MAC filtering by peer?)
May 10 15:22:54 thomas-desktop kernel: [ 1407.153359] wlan0: association FAILED: peer sent Status Code 12 (Assoc denied (reason outside of 802.11b scope) -- maybe MAC filtering by peer?)
May 10 15:22:56 thomas-desktop kernel: [ 1409.652618] wlan0: association FAILED: peer sent Status Code 12 (Assoc denied (reason outside of 802.11b scope) -- maybe MAC filtering by peer?)
May 10 15:22:59 thomas-desktop kernel: [ 1412.151864] wlan0: association FAILED: peer sent Status Code 12 (Assoc denied (reason outside of 802.11b scope) -- maybe MAC filtering by peer?)
May 10 15:23:01 thomas-desktop kernel: [ 1414.651139] wlan0: association FAILED: peer sent Status Code 12 (Assoc denied (reason outside of 802.11b scope) -- maybe MAC filtering by peer?)
May 10 15:23:04 thomas-desktop kernel: [ 1417.150390] wlan0: association FAILED: peer sent Status Code 12 (Assoc denied (reason outside of 802.11b scope) -- maybe MAC filtering by peer?)
May 10 15:23:08 thomas-desktop kernel: [ 1421.908262] wlan0: association FAILED: peer sent Status Code 12 (Assoc denied (reason outside of 802.11b scope) -- maybe MAC filtering by peer?)
May 10 15:23:10 thomas-desktop kernel: [ 1423.404380] wlan0: association FAILED: peer sent Status Code 12 (Assoc denied (reason outside of 802.11b scope) -- maybe MAC filtering by peer?)
May 10 15:23:12 thomas-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/wlan0 for sub-path wlan0.dbus.get.reason
May 10 15:23:15 thomas-desktop kernel: [ 1428.465553] wlan0: association FAILED: peer sent Status Code 12 (Assoc denied (reason outside of 802.11b scope) -- maybe MAC filtering by peer?)
May 10 15:23:17 thomas-desktop kernel: [ 1429.963583] wlan0: association FAILED: peer sent Status Code 12 (Assoc denied (reason outside of 802.11b scope) -- maybe MAC filtering by peer?)
May 10 15:23:19 thomas-desktop kernel: [ 1432.461875] wlan0: association FAILED: peer sent Status Code 12 (Assoc denied (reason outside of 802.11b scope) -- maybe MAC filtering by peer?)
May 10 15:23:22 thomas-desktop kernel: [ 1434.961123] wlan0: association FAILED: peer sent Status Code 12 (Assoc denied (reason outside of 802.11b scope) -- maybe MAC filtering by peer?)
May 10 15:23:24 thomas-desktop kernel: [ 1437.460386] wlan0: association FAILED: peer sent Status Code 12 (Assoc denied (reason outside of 802.11b scope) -- maybe MAC filtering by peer?)
May 10 15:23:27 thomas-desktop kernel: [ 1439.959648] wlan0: association FAILED: peer sent Status Code 12 (Assoc denied (reason outside of 802.11b scope) -- maybe MAC filtering by peer?)
May 10 15:23:29 thomas-desktop kernel: [ 1442.459485] wlan0: association FAILED: peer sent Status Code 12 (Assoc denied (reason outside of 802.11b scope) -- maybe MAC filtering by peer?)
May 10 15:23:32 thomas-desktop kernel: [ 1444.958180] wlan0: association FAILED: peer sent Status Code 12 (Assoc denied (reason outside of 802.11b scope) -- maybe MAC filtering by peer?)
May 10 15:23:34 thomas-desktop kernel: [ 1447.457438] wlan0: association FAILED: peer sent Status Code 12 (Assoc denied (reason outside of 802.11b scope) -- maybe MAC filtering by peer?)
May 10 15:23:37 thomas-desktop kernel: [ 1449.956680] wlan0: association FAILED: peer sent Status Code 12 (Assoc denied (reason outside of 802.11b scope) -- maybe MAC filtering by peer?)
May 10 15:23:41 thomas-desktop kernel: [ 1454.714459] wlan0: association FAILED: peer sent Status Code 12 (Assoc denied (reason outside of 802.11b scope) -- maybe MAC filtering by peer?)
May 10 15:23:43 thomas-desktop kernel: [ 1456.210666] wlan0: association FAILED: peer sent Status Code 12 (Assoc denied (reason outside of 802.11b scope) -- maybe MAC filtering by peer?)
May 10 15:23:45 thomas-desktop kernel: [ 1458.709919] wlan0: association FAILED: peer sent Status Code 12 (Assoc denied (reason outside of 802.11b scope) -- maybe MAC filtering by peer?)
May 10 15:23:48 thomas-desktop kernel: [ 1461.209181] wlan0: association FAILED: peer sent Status Code 12 (Assoc denied (reason outside of 802.11b scope) -- maybe MAC filtering by peer?)
May 10 15:23:50 thomas-desktop kernel: [ 1463.709093] wlan0: association FAILED: peer sent Status Code 12 (Assoc denied (reason outside of 802.11b scope) -- maybe MAC filtering by peer?)
May 10 15:23:53 thomas-desktop kernel: [ 1466.207719] wlan0: association FAILED: peer sent Status Code 12 (Assoc denied (reason outside of 802.11b scope) -- maybe MAC filtering by peer?)
May 10 15:23:55 thomas-desktop kernel: [ 1469.696675] wlan0: association FAILED: peer sent Status Code 12 (Assoc denied (reason outside of 802.11b scope) -- maybe MAC filtering by peer?)
May 10 15:23:57 thomas-desktop kernel: [ 1472.577047] NET: Registered protocol family 17
May 10 15:24:02 thomas-desktop kernel: [ 1478.956604] wlan0: issue_cmd(): timed out waiting for CMD_COMPLETE. irq bits:0x0000 irq_status:0x0000 timeout:49ms cmd_status:1 (Success)
May 10 15:24:02 thomas-desktop kernel: [ 1478.956614] wlan0: issue_cmd(cmd:0x0016) FAILED
May 10 15:24:02 thomas-desktop kernel: [ 1478.956621] Pid: 13513, comm: wpa_supplicant Not tainted 2.6.24-16-generic #1
May 10 15:24:02 thomas-desktop kernel: [ 1478.956652]  [<cca78c4f>] acxpci_s_issue_cmd_timeo+0x2af/0x3a0 [acx]
May 10 15:24:02 thomas-desktop kernel: [ 1478.956748]  [<cca708a8>] acx_s_set_probe_request_template+0x138/0x170 [acx]
May 10 15:24:02 thomas-desktop kernel: [ 1478.956852]  [<cca6e8e0>] acx_ioctl_commit+0x0/0x40 [acx]
May 10 15:24:02 thomas-desktop kernel: [ 1478.956876]  [<cca726be>] acx_s_update_card_settings+0xa3e/0xd10 [acx]
May 10 15:24:02 thomas-desktop kernel: [ 1478.956900]  [agpgart:__alloc_pages+0x60/0x390] __alloc_pages+0x60/0x390
May 10 15:24:02 thomas-desktop kernel: [ 1478.956968]  [__nla_put+0x19/0x40] __nla_put+0x19/0x40
May 10 15:24:02 thomas-desktop kernel: [ 1478.956992]  [skb_queue_tail+0x1c/0x50] skb_queue_tail+0x1c/0x50
May 10 15:24:02 thomas-desktop kernel: [ 1478.957010]  [acx:wireless_send_event+0x241/0xf70] wireless_send_event+0x241/0x370
May 10 15:24:02 thomas-desktop kernel: [ 1478.957028]  [enqueue_entity+0x2b/0x60] enqueue_entity+0x2b/0x60
May 10 15:24:02 thomas-desktop kernel: [ 1478.957041]  [<cca6e8e0>] acx_ioctl_commit+0x0/0x40 [acx]
May 10 15:24:02 thomas-desktop kernel: [ 1478.957065]  [<cca6e908>] acx_ioctl_commit+0x28/0x40 [acx]
May 10 15:24:02 thomas-desktop kernel: [ 1478.957083]  [call_commit_handler+0x32/0x50] call_commit_handler+0x32/0x50
May 10 15:24:02 thomas-desktop kernel: [ 1478.957100]  [ioctl_standard_call+0x28a/0x370] ioctl_standard_call+0x28a/0x370
May 10 15:24:02 thomas-desktop kernel: [ 1478.957118]  [ide_core:kunmap_atomic+0x3d/0x29e0] kunmap_atomic+0x3d/0xb0
May 10 15:24:02 thomas-desktop kernel: [ 1478.957150]  [snd_pcm:mutex_lock+0x8/0x290] mutex_lock+0x8/0x20
May 10 15:24:02 thomas-desktop kernel: [ 1478.957164]  [__dev_get_by_name+0x74/0x90] __dev_get_by_name+0x74/0x90
May 10 15:24:02 thomas-desktop kernel: [ 1478.957205]  [wext_handle_ioctl+0x3ac/0x440] wext_handle_ioctl+0x3ac/0x440
May 10 15:24:02 thomas-desktop kernel: [ 1478.957213]  [<cca6f140>] acx_ioctl_set_encode+0x0/0x170 [acx]
May 10 15:24:02 thomas-desktop kernel: [ 1478.957237]  [<cca6f140>] acx_ioctl_set_encode+0x0/0x170 [acx]
May 10 15:24:02 thomas-desktop kernel: [ 1478.957263]  [unmap_vmas+0x400/0x610] unmap_vmas+0x400/0x610
May 10 15:24:02 thomas-desktop kernel: [ 1478.957285]  [dev_ioctl+0x4c1/0x500] dev_ioctl+0x4c1/0x500
May 10 15:24:02 thomas-desktop kernel: [ 1478.957341]  [free_pgtables+0x85/0xc0] free_pgtables+0x85/0xc0
May 10 15:24:02 thomas-desktop kernel: [ 1478.957396]  [sock_ioctl+0x0/0x220] sock_ioctl+0x0/0x220
May 10 15:24:02 thomas-desktop kernel: [ 1478.957415]  [do_ioctl+0x2b/0x90] do_ioctl+0x2b/0x90
May 10 15:24:02 thomas-desktop kernel: [ 1478.957440]  [vfs_ioctl+0x22e/0x2b0] vfs_ioctl+0x22e/0x2b0
May 10 15:24:02 thomas-desktop kernel: [ 1478.957468]  [sys_ioctl+0x56/0x70] sys_ioctl+0x56/0x70
May 10 15:24:02 thomas-desktop kernel: [ 1478.957488]  [sysenter_past_esp+0x6b/0xa9] sysenter_past_esp+0x6b/0xa9
May 10 15:24:02 thomas-desktop kernel: [ 1478.957563]  =======================
May 10 15:25:28 thomas-desktop kernel: [ 1564.931138] wlan0: issue_cmd(): timed out waiting for CMD_COMPLETE. irq bits:0x0000 irq_status:0x0000 timeout:49ms cmd_status:1 (Success)
May 10 15:25:28 thomas-desktop kernel: [ 1564.931148] wlan0: issue_cmd(cmd:0x0016) FAILED
May 10 15:25:28 thomas-desktop kernel: [ 1564.931154] Pid: 14500, comm: wpa_supplicant Not tainted 2.6.24-16-generic #1
May 10 15:25:28 thomas-desktop kernel: [ 1564.931183]  [<cca78c4f>] acxpci_s_issue_cmd_timeo+0x2af/0x3a0 [acx]
May 10 15:25:28 thomas-desktop kernel: [ 1564.931277]  [<cca708a8>] acx_s_set_probe_request_template+0x138/0x170 [acx]
May 10 15:25:28 thomas-desktop kernel: [ 1564.931378]  [<cca6e8e0>] acx_ioctl_commit+0x0/0x40 [acx]
May 10 15:25:28 thomas-desktop kernel: [ 1564.931402]  [<cca726be>] acx_s_update_card_settings+0xa3e/0xd10 [acx]
May 10 15:25:28 thomas-desktop kernel: [ 1564.931425]  [agpgart:__alloc_pages+0x60/0x390] __alloc_pages+0x60/0x390
May 10 15:25:28 thomas-desktop kernel: [ 1564.931489]  [__nla_put+0x19/0x40] __nla_put+0x19/0x40
May 10 15:25:28 thomas-desktop kernel: [ 1564.931512]  [skb_queue_tail+0x1c/0x50] skb_queue_tail+0x1c/0x50
May 10 15:25:28 thomas-desktop kernel: [ 1564.931530]  [acx:wireless_send_event+0x241/0xf70] wireless_send_event+0x241/0x370
May 10 15:25:28 thomas-desktop kernel: [ 1564.931544]  [ip_tables:copy_from_user+0x2e/0x280] copy_from_user+0x2e/0x70
May 10 15:25:28 thomas-desktop kernel: [ 1564.931561]  [<cca6e8e0>] acx_ioctl_commit+0x0/0x40 [acx]
May 10 15:25:28 thomas-desktop kernel: [ 1564.931584]  [<cca6e908>] acx_ioctl_commit+0x28/0x40 [acx]
May 10 15:25:28 thomas-desktop kernel: [ 1564.931602]  [call_commit_handler+0x32/0x50] call_commit_handler+0x32/0x50
May 10 15:25:28 thomas-desktop kernel: [ 1564.931619]  [ioctl_standard_call+0x28a/0x370] ioctl_standard_call+0x28a/0x370
May 10 15:25:28 thomas-desktop kernel: [ 1564.931635]  [ide_core:kunmap_atomic+0x3d/0x29e0] kunmap_atomic+0x3d/0xb0
May 10 15:25:28 thomas-desktop kernel: [ 1564.931667]  [snd_pcm:mutex_lock+0x8/0x290] mutex_lock+0x8/0x20
May 10 15:25:28 thomas-desktop kernel: [ 1564.931679]  [__dev_get_by_name+0x74/0x90] __dev_get_by_name+0x74/0x90
May 10 15:25:28 thomas-desktop kernel: [ 1564.931719]  [wext_handle_ioctl+0x3ac/0x440] wext_handle_ioctl+0x3ac/0x440
May 10 15:25:28 thomas-desktop kernel: [ 1564.931726]  [<cca6f140>] acx_ioctl_set_encode+0x0/0x170 [acx]
May 10 15:25:28 thomas-desktop kernel: [ 1564.931750]  [<cca6f140>] acx_ioctl_set_encode+0x0/0x170 [acx]
May 10 15:25:28 thomas-desktop kernel: [ 1564.931775]  [unmap_vmas+0x400/0x610] unmap_vmas+0x400/0x610
May 10 15:25:28 thomas-desktop kernel: [ 1564.931796]  [dev_ioctl+0x4c1/0x500] dev_ioctl+0x4c1/0x500
May 10 15:25:28 thomas-desktop kernel: [ 1564.931849]  [free_pgtables+0x85/0xc0] free_pgtables+0x85/0xc0
May 10 15:25:28 thomas-desktop kernel: [ 1564.931902]  [sock_ioctl+0x0/0x220] sock_ioctl+0x0/0x220
May 10 15:25:28 thomas-desktop kernel: [ 1564.931920]  [do_ioctl+0x2b/0x90] do_ioctl+0x2b/0x90
May 10 15:25:28 thomas-desktop kernel: [ 1564.931944]  [vfs_ioctl+0x22e/0x2b0] vfs_ioctl+0x22e/0x2b0
May 10 15:25:28 thomas-desktop kernel: [ 1564.931971]  [sys_ioctl+0x56/0x70] sys_ioctl+0x56/0x70
May 10 15:25:28 thomas-desktop kernel: [ 1564.931990]  [sysenter_past_esp+0x6b/0xa9] sysenter_past_esp+0x6b/0xa9
May 10 15:25:28 thomas-desktop kernel: [ 1564.932061]  =======================
May 10 15:25:30 thomas-desktop kernel: [ 1567.482406] wlan0: issue_cmd(): timed out waiting for CMD_COMPLETE. irq bits:0x0000 irq_status:0x0000 timeout:49ms cmd_status:1 (Success)
May 10 15:25:30 thomas-desktop kernel: [ 1567.482417] wlan0: issue_cmd(cmd:0x0002) FAILED
May 10 15:25:30 thomas-desktop kernel: [ 1567.482423] Pid: 14500, comm: wpa_supplicant Not tainted 2.6.24-16-generic #1
May 10 15:25:30 thomas-desktop kernel: [ 1567.482451]  [<cca78c4f>] acxpci_s_issue_cmd_timeo+0x2af/0x3a0 [acx]
May 10 15:25:30 thomas-desktop kernel: [ 1567.482538]  [<cca70e74>] acx_s_configure+0x54/0xc0 [acx]
May 10 15:25:30 thomas-desktop kernel: [ 1567.482571]  [<cca6e8e0>] acx_ioctl_commit+0x0/0x40 [acx]
May 10 15:25:30 thomas-desktop kernel: [ 1567.482592]  [<cca72109>] acx_s_update_card_settings+0x489/0xd10 [acx]
May 10 15:25:30 thomas-desktop kernel: [ 1567.482616]  [agpgart:__alloc_pages+0x60/0x390] __alloc_pages+0x60/0x390
May 10 15:25:30 thomas-desktop kernel: [ 1567.482680]  [__nla_put+0x19/0x40] __nla_put+0x19/0x40
May 10 15:25:30 thomas-desktop kernel: [ 1567.482703]  [skb_queue_tail+0x1c/0x50] skb_queue_tail+0x1c/0x50
May 10 15:25:30 thomas-desktop kernel: [ 1567.482731]  [ip_tables:copy_from_user+0x2e/0x280] copy_from_user+0x2e/0x70
May 10 15:25:30 thomas-desktop kernel: [ 1567.482748]  [<cca6e8e0>] acx_ioctl_commit+0x0/0x40 [acx]
May 10 15:25:30 thomas-desktop kernel: [ 1567.482771]  [<cca6e908>] acx_ioctl_commit+0x28/0x40 [acx]
May 10 15:25:30 thomas-desktop kernel: [ 1567.482788]  [call_commit_handler+0x32/0x50] call_commit_handler+0x32/0x50
May 10 15:25:30 thomas-desktop kernel: [ 1567.482806]  [ioctl_standard_call+0x28a/0x370] ioctl_standard_call+0x28a/0x370
May 10 15:25:30 thomas-desktop kernel: [ 1567.482823]  [ide_core:kunmap_atomic+0x3d/0x29e0] kunmap_atomic+0x3d/0xb0
May 10 15:25:30 thomas-desktop kernel: [ 1567.482854]  [snd_pcm:mutex_lock+0x8/0x290] mutex_lock+0x8/0x20
May 10 15:25:30 thomas-desktop kernel: [ 1567.482867]  [__dev_get_by_name+0x74/0x90] __dev_get_by_name+0x74/0x90
May 10 15:25:30 thomas-desktop kernel: [ 1567.482907]  [wext_handle_ioctl+0x3ac/0x440] wext_handle_ioctl+0x3ac/0x440
May 10 15:25:30 thomas-desktop kernel: [ 1567.482915]  [<cca6f140>] acx_ioctl_set_encode+0x0/0x170 [acx]
May 10 15:25:30 thomas-desktop kernel: [ 1567.482938]  [<cca6f140>] acx_ioctl_set_encode+0x0/0x170 [acx]
May 10 15:25:30 thomas-desktop kernel: [ 1567.482962]  [unmap_vmas+0x400/0x610] unmap_vmas+0x400/0x610
May 10 15:25:30 thomas-desktop kernel: [ 1567.482983]  [dev_ioctl+0x4c1/0x500] dev_ioctl+0x4c1/0x500
May 10 15:25:30 thomas-desktop kernel: [ 1567.483036]  [free_pgtables+0x85/0xc0] free_pgtables+0x85/0xc0
May 10 15:25:30 thomas-desktop kernel: [ 1567.483089]  [sock_ioctl+0x0/0x220] sock_ioctl+0x0/0x220
May 10 15:25:30 thomas-desktop kernel: [ 1567.483106]  [do_ioctl+0x2b/0x90] do_ioctl+0x2b/0x90
May 10 15:25:30 thomas-desktop kernel: [ 1567.483130]  [vfs_ioctl+0x22e/0x2b0] vfs_ioctl+0x22e/0x2b0
May 10 15:25:30 thomas-desktop kernel: [ 1567.483157]  [sys_ioctl+0x56/0x70] sys_ioctl+0x56/0x70
May 10 15:25:30 thomas-desktop kernel: [ 1567.483176]  [sysenter_past_esp+0x6b/0xa9] sysenter_past_esp+0x6b/0xa9
May 10 15:25:30 thomas-desktop kernel: [ 1567.483247]  =======================
May 10 15:25:30 thomas-desktop kernel: [ 1567.483251] wlan0: configure(type:0x1010) FAILED
May 10 15:26:08 thomas-desktop kernel: [ 1609.660036] usb 2-3: new full speed USB device using ohci_hcd and address 3
May 10 15:26:09 thomas-desktop kernel: [ 1609.869201] usb 2-3: configuration #1 chosen from 1 choice
May 10 15:26:11 thomas-desktop kernel: [ 1612.231561] usbcore: registered new interface driver libusual
May 10 15:26:11 thomas-desktop kernel: [ 1612.346655] Initializing USB Mass Storage driver...
May 10 15:26:11 thomas-desktop kernel: [ 1612.349674] scsi2 : SCSI emulation for USB Mass Storage devices
May 10 15:26:11 thomas-desktop kernel: [ 1612.352491] usbcore: registered new interface driver usb-storage
May 10 15:26:11 thomas-desktop kernel: [ 1612.353394] USB Mass Storage support registered.
May 10 15:26:16 thomas-desktop kernel: [ 1617.358309] scsi 2:0:0:0: Direct-Access     PHILIPS  Key Audio 128MB  0100 PQ: 0 ANSI: 4
May 10 15:26:16 thomas-desktop kernel: [ 1617.532403] Driver 'sd' needs updating - please use bus_type methods
May 10 15:26:16 thomas-desktop kernel: [ 1617.542225] sd 2:0:0:0: [sda] 250112 512-byte hardware sectors (128 MB)
May 10 15:26:16 thomas-desktop kernel: [ 1617.548213] sd 2:0:0:0: [sda] Write Protect is off
May 10 15:26:16 thomas-desktop kernel: [ 1617.574210] sd 2:0:0:0: [sda] 250112 512-byte hardware sectors (128 MB)
May 10 15:26:16 thomas-desktop kernel: [ 1617.580206] sd 2:0:0:0: [sda] Write Protect is off
May 10 15:26:16 thomas-desktop kernel: [ 1617.580229]  sda: sda1
May 10 15:26:16 thomas-desktop kernel: [ 1617.590431] sd 2:0:0:0: [sda] Attached SCSI removable disk
May 10 15:26:16 thomas-desktop kernel: [ 1617.722250] sd 2:0:0:0: Attached scsi generic sg0 type 0
May 10 15:26:26 thomas-desktop kernel: [ 1627.570728] wlan0: issue_cmd(): timed out waiting for CMD_COMPLETE. irq bits:0x0000 irq_status:0x0000 timeout:49ms cmd_status:1 (Success)
May 10 15:26:26 thomas-desktop kernel: [ 1627.570739] wlan0: issue_cmd(cmd:0x0016) FAILED
May 10 15:26:26 thomas-desktop kernel: [ 1627.570745] Pid: 14500, comm: wpa_supplicant Not tainted 2.6.24-16-generic #1
May 10 15:26:26 thomas-desktop kernel: [ 1627.570778]  [<cca78c4f>] acxpci_s_issue_cmd_timeo+0x2af/0x3a0 [acx]
May 10 15:26:26 thomas-desktop kernel: [ 1627.570890]  [<cca708a8>] acx_s_set_probe_request_template+0x138/0x170 [acx]
May 10 15:26:26 thomas-desktop kernel: [ 1627.571012]  [<cca6e8e0>] acx_ioctl_commit+0x0/0x40 [acx]
May 10 15:26:26 thomas-desktop kernel: [ 1627.571038]  [<cca726be>] acx_s_update_card_settings+0xa3e/0xd10 [acx]
May 10 15:26:26 thomas-desktop kernel: [ 1627.571064]  [agpgart:__alloc_pages+0x60/0x390] __alloc_pages+0x60/0x390
May 10 15:26:26 thomas-desktop kernel: [ 1627.571143]  [__nla_put+0x19/0x40] __nla_put+0x19/0x40
May 10 15:26:26 thomas-desktop kernel: [ 1627.571169]  [skb_queue_tail+0x1c/0x50] skb_queue_tail+0x1c/0x50
May 10 15:26:26 thomas-desktop kernel: [ 1627.571189]  [acx:wireless_send_event+0x241/0xf70] wireless_send_event+0x241/0x370
May 10 15:26:26 thomas-desktop kernel: [ 1627.571223]  [<cca6e8e0>] acx_ioctl_commit+0x0/0x40 [acx]
May 10 15:26:26 thomas-desktop kernel: [ 1627.571248]  [<cca6e908>] acx_ioctl_commit+0x28/0x40 [acx]
May 10 15:26:26 thomas-desktop kernel: [ 1627.571267]  [call_commit_handler+0x32/0x50] call_commit_handler+0x32/0x50
May 10 15:26:26 thomas-desktop kernel: [ 1627.571287]  [ioctl_standard_call+0x28a/0x370] ioctl_standard_call+0x28a/0x370
May 10 15:26:26 thomas-desktop kernel: [ 1627.571307]  [ide_core:kunmap_atomic+0x3d/0x29e0] kunmap_atomic+0x3d/0xb0
May 10 15:26:26 thomas-desktop kernel: [ 1627.571346]  [snd_pcm:mutex_lock+0x8/0x290] mutex_lock+0x8/0x20
May 10 15:26:26 thomas-desktop kernel: [ 1627.571361]  [__dev_get_by_name+0x74/0x90] __dev_get_by_name+0x74/0x90
May 10 15:26:26 thomas-desktop kernel: [ 1627.571409]  [wext_handle_ioctl+0x3ac/0x440] wext_handle_ioctl+0x3ac/0x440
May 10 15:26:26 thomas-desktop kernel: [ 1627.571418]  [<cca6f140>] acx_ioctl_set_encode+0x0/0x170 [acx]
May 10 15:26:26 thomas-desktop kernel: [ 1627.571444]  [<cca6f140>] acx_ioctl_set_encode+0x0/0x170 [acx]
May 10 15:26:26 thomas-desktop kernel: [ 1627.571473]  [unmap_vmas+0x400/0x610] unmap_vmas+0x400/0x610
May 10 15:26:26 thomas-desktop kernel: [ 1627.571498]  [dev_ioctl+0x4c1/0x500] dev_ioctl+0x4c1/0x500
May 10 15:26:26 thomas-desktop kernel: [ 1627.571564]  [free_pgtables+0x85/0xc0] free_pgtables+0x85/0xc0
May 10 15:26:26 thomas-desktop kernel: [ 1627.571629]  [sock_ioctl+0x0/0x220] sock_ioctl+0x0/0x220
May 10 15:26:26 thomas-desktop kernel: [ 1627.571650]  [do_ioctl+0x2b/0x90] do_ioctl+0x2b/0x90
May 10 15:26:26 thomas-desktop kernel: [ 1627.571679]  [vfs_ioctl+0x22e/0x2b0] vfs_ioctl+0x22e/0x2b0
May 10 15:26:26 thomas-desktop kernel: [ 1627.571712]  [sys_ioctl+0x56/0x70] sys_ioctl+0x56/0x70
May 10 15:26:26 thomas-desktop kernel: [ 1627.571735]  [sysenter_past_esp+0x6b/0xa9] sysenter_past_esp+0x6b/0xa9
May 10 15:26:26 thomas-desktop kernel: [ 1627.571824]  =======================
May 10 15:27:43 thomas-desktop kernel: [ 1715.949835] UDF-fs: No VRS found
May 10 15:27:56 thomas-desktop kernel: [ 1728.829312] wlan0: tx error 0x08, buf 09! (WEP key not found)
May 10 15:28:48 thomas-desktop kernel: [ 1780.719833] wlan0: issue_cmd(): timed out waiting for CMD_COMPLETE. irq bits:0x0000 irq_status:0x0000 timeout:49ms cmd_status:1 (Success)
May 10 15:28:48 thomas-desktop kernel: [ 1780.719843] wlan0: issue_cmd(cmd:0x0016) FAILED
May 10 15:28:48 thomas-desktop kernel: [ 1780.719849] Pid: 14500, comm: wpa_supplicant Not tainted 2.6.24-16-generic #1
May 10 15:28:48 thomas-desktop kernel: [ 1780.719883]  [<cca78c4f>] acxpci_s_issue_cmd_timeo+0x2af/0x3a0 [acx]
May 10 15:28:48 thomas-desktop kernel: [ 1780.719998]  [<cca708a8>] acx_s_set_probe_request_template+0x138/0x170 [acx]
May 10 15:28:48 thomas-desktop kernel: [ 1780.720123]  [<cca6e8e0>] acx_ioctl_commit+0x0/0x40 [acx]
May 10 15:28:48 thomas-desktop kernel: [ 1780.720150]  [<cca726be>] acx_s_update_card_settings+0xa3e/0xd10 [acx]
May 10 15:28:48 thomas-desktop kernel: [ 1780.720177]  [agpgart:__alloc_pages+0x60/0x390] __alloc_pages+0x60/0x390
May 10 15:28:48 thomas-desktop kernel: [ 1780.720258]  [__nla_put+0x19/0x40] __nla_put+0x19/0x40
May 10 15:28:48 thomas-desktop kernel: [ 1780.720285]  [skb_queue_tail+0x1c/0x50] skb_queue_tail+0x1c/0x50
May 10 15:28:48 thomas-desktop kernel: [ 1780.720306]  [acx:wireless_send_event+0x241/0xf70] wireless_send_event+0x241/0x370
May 10 15:28:48 thomas-desktop kernel: [ 1780.720339]  [<cca6e8e0>] acx_ioctl_commit+0x0/0x40 [acx]
May 10 15:28:48 thomas-desktop kernel: [ 1780.720367]  [<cca6e908>] acx_ioctl_commit+0x28/0x40 [acx]
May 10 15:28:48 thomas-desktop kernel: [ 1780.720386]  [call_commit_handler+0x32/0x50] call_commit_handler+0x32/0x50
May 10 15:28:48 thomas-desktop kernel: [ 1780.720406]  [ioctl_standard_call+0x28a/0x370] ioctl_standard_call+0x28a/0x370
May 10 15:28:48 thomas-desktop kernel: [ 1780.720426]  [ide_core:kunmap_atomic+0x3d/0x29e0] kunmap_atomic+0x3d/0xb0
May 10 15:28:48 thomas-desktop kernel: [ 1780.720466]  [snd_pcm:mutex_lock+0x8/0x290] mutex_lock+0x8/0x20
May 10 15:28:48 thomas-desktop kernel: [ 1780.720481]  [__dev_get_by_name+0x74/0x90] __dev_get_by_name+0x74/0x90
May 10 15:28:48 thomas-desktop kernel: [ 1780.720529]  [wext_handle_ioctl+0x3ac/0x440] wext_handle_ioctl+0x3ac/0x440
May 10 15:28:48 thomas-desktop kernel: [ 1780.720537]  [<cca6f140>] acx_ioctl_set_encode+0x0/0x170 [acx]
May 10 15:28:48 thomas-desktop kernel: [ 1780.720564]  [<cca6f140>] acx_ioctl_set_encode+0x0/0x170 [acx]
May 10 15:28:48 thomas-desktop kernel: [ 1780.720592]  [unmap_vmas+0x400/0x610] unmap_vmas+0x400/0x610
May 10 15:28:48 thomas-desktop kernel: [ 1780.720617]  [dev_ioctl+0x4c1/0x500] dev_ioctl+0x4c1/0x500
May 10 15:28:48 thomas-desktop kernel: [ 1780.720683]  [free_pgtables+0x85/0xc0] free_pgtables+0x85/0xc0
May 10 15:28:48 thomas-desktop kernel: [ 1780.720748]  [sock_ioctl+0x0/0x220] sock_ioctl+0x0/0x220
May 10 15:28:48 thomas-desktop kernel: [ 1780.720769]  [do_ioctl+0x2b/0x90] do_ioctl+0x2b/0x90
May 10 15:28:48 thomas-desktop kernel: [ 1780.720797]  [vfs_ioctl+0x22e/0x2b0] vfs_ioctl+0x22e/0x2b0
May 10 15:28:48 thomas-desktop kernel: [ 1780.720830]  [sys_ioctl+0x56/0x70] sys_ioctl+0x56/0x70
May 10 15:28:48 thomas-desktop kernel: [ 1780.720853]  [sysenter_past_esp+0x6b/0xa9] sysenter_past_esp+0x6b/0xa9
May 10 15:28:48 thomas-desktop kernel: [ 1780.720942]  =======================
[/quote]

Also contains my failed attempts at trying to logon to my WLAN via failsafe gnome...thats another problem I'll need to combat later.

[quote=Xorg.0.log][noparse]
This is a pre-release version of the X server from The X.Org Foundation.
It is not supported in any way.
Bugs may be filed in the bugzilla at [http://bugs.freedesktop.org/](http://bugs.freedesktop.org/).
Select the "xorg" product for bugs you find in this release.
Before reporting bugs in pre-release versions please check the
latest version in the X.Org Foundation git repository.
See [http://wiki.x.org/wiki/GitPage](http://wiki.x.org/wiki/GitPage) for git access instructions.

X.Org X Server 1.4.0.90
Release Date: 5 September 2007
X Protocol Version 11, Revision 0
Build Operating System: Linux Ubuntu (xorg-server 2:1.4.1~git20080131-1ubuntu9)
Current Operating System: Linux thomas-desktop 2.6.24-16-generic #1 SMP Thu Apr 10 13:23:42 UTC 2008 i686
Build Date: 15 April 2008  05:26:17PM
 
	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sat May 10 15:22:00 2008
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Configured Monitor"
(**) |   |-->Device "Configured Video Device"
(==) Automatically adding devices
(==) Automatically enabling devices
(==) No FontPath specified.  Using compiled-in default.
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType
(==) RgbPath set to "/etc/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(==) |-->Input Device "Configured Mouse"
(==) |-->Input Device "Generic Keyboard"
(==) The core pointer device wasn't specified explicitly in the layout.
	Using the first core pointer device.
(==) The core keyboard device wasn't specified explicitly in the layout.
	Using the first keyboard device.
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Loader magic: 0x81dc500
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.3
	X.Org Video Driver: 2.0
	X.Org XInput driver : 2.0
	X.Org Server Extension : 0.3
	X.Org Font Renderer : 0.5
(II) Loader running on linux
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules//libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Video Driver, version 2.0
(++) using VT number 9

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 1002,5950 card 103c,2a24 rev 10 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 1002,5a3f card 0000,0000 rev 00 class 06,04,00 hdr 01
(II) PCI: 00:12:0: chip 1002,4379 card 103c,2a24 rev 00 class 01,01,8f hdr 00
(II) PCI: 00:13:0: chip 1002,4374 card 103c,2a24 rev 00 class 0c,03,10 hdr 80
(II) PCI: 00:13:1: chip 1002,4375 card 103c,2a24 rev 00 class 0c,03,10 hdr 00
(II) PCI: 00:13:2: chip 1002,4373 card 103c,2a24 rev 00 class 0c,03,20 hdr 00
(II) PCI: 00:14:0: chip 1002,4372 card 103c,2a24 rev 11 class 0c,05,00 hdr 80
(II) PCI: 00:14:1: chip 1002,4376 card 103c,2a24 rev 00 class 01,01,8a hdr 00
(II) PCI: 00:14:3: chip 1002,4377 card 103c,2a24 rev 00 class 06,01,00 hdr 80
(II) PCI: 00:14:4: chip 1002,4371 card 0000,0000 rev 00 class 06,04,01 hdr 81
(II) PCI: 00:14:5: chip 1002,4370 card 103c,2a25 rev 02 class 04,01,00 hdr 80
(II) PCI: 00:18:0: chip 1022,1100 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:1: chip 1022,1101 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:2: chip 1022,1102 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:3: chip 1022,1103 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 01:05:0: chip 1002,5954 card 103c,2a24 rev 00 class 03,00,00 hdr 00
(II) PCI: 02:01:0: chip 11c1,048c card 11c1,044c rev 03 class 07,80,00 hdr 00
(II) PCI: 02:02:0: chip 104c,8400 card 1186,3b01 rev 00 class 02,80,00 hdr 00
(II) PCI: 02:03:0: chip 10ec,8139 card 103c,2a24 rev 10 class 02,00,00 hdr 00
(II) PCI: 02:04:0: chip 1106,3044 card 103c,2a24 rev 80 class 0c,00,10 hdr 00
(II) PCI: End of PCI scan
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,2), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x000a (VGA_EN is set)
(II) Bus 1 I/O range:
	[0] -1	0	0x0000e000 - 0x0000efff (0x1000) IX[B]
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xfdd00000 - 0xfddfffff (0x100000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xd8000000 - 0xdfffffff (0x8000000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:20:3), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:20:4), (0,2,2), BCTRL: 0x0002 (VGA_EN is cleared)
(II) Bus 2 I/O range:
	[0] -1	0	0x0000d000 - 0x0000dfff (0x1000) IX[B]
(II) Bus 2 non-prefetchable memory range:
	[0] -1	0	0xfdc00000 - 0xfdcfffff (0x100000) MX[B]
(II) Bus 2 prefetchable memory range:
	[0] -1	0	0xfde00000 - 0xfdefffff (0x100000) MX[B]
(--) PCI:*(1:5:0) ATI Technologies Inc RS480 [Radeon Xpress 200G Series] rev 0, Mem @ 0xd8000000/27, 0xfddf0000/16, I/O @ 0xef00/8
(II) Addressable bus resource ranges are
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
	[1] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) OS-reported resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) PCI I/O resource overlap reduced 0x00004100 from 0x0000411f to 0x000040ff
(II) PCI Memory resource overlap reduced 0xe0000000 from 0xe0000000 to 0xdfffffff
(II) Active PCI resource ranges:
	[0] -1	0	0xfdcfc000 - 0xfdcfc7ff (0x800) MX[B]
	[1] -1	0	0xfdcfd000 - 0xfdcfd0ff (0x100) MX[B]
	[2] -1	0	0xfdce0000 - 0xfdceffff (0x10000) MX[B]
	[3] -1	0	0xfdcfe000 - 0xfdcfefff (0x1000) MX[B]
	[4] -1	0	0xfdcff000 - 0xfdcff0ff (0x100) MX[B]
	[5] -1	0	0xfe02a000 - 0xfe02a0ff (0x100) MX[B]
	[6] -1	0	0xfe02b000 - 0xfe02b3ff (0x400) MX[B]
	[7] -1	0	0xfe02c000 - 0xfe02cfff (0x1000) MX[B]
	[8] -1	0	0xfe02d000 - 0xfe02dfff (0x1000) MX[B]
	[9] -1	0	0xfe02e000 - 0xfe02efff (0x1000) MX[B]
	[10] -1	0	0xfe02f000 - 0xfe02f1ff (0x200) MX[B]
	[11] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[12] -1	0	0xfddf0000 - 0xfddfffff (0x10000) MX[B](B)
	[13] -1	0	0xd8000000 - 0xdfffffff (0x8000000) MX[B](B)
	[14] -1	0	0x0000db00 - 0x0000db7f (0x80) IX[B]
	[15] -1	0	0x0000dc00 - 0x0000dcff (0x100) IX[B]
	[16] -1	0	0x0000dd00 - 0x0000dd1f (0x20) IX[B]
	[17] -1	0	0x0000de00 - 0x0000deff (0x100) IX[B]
	[18] -1	0	0x0000df00 - 0x0000df07 (0x8) IX[B]
	[19] -1	0	0x0000f800 - 0x0000f80f (0x10) IX[B]
	[20] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[21] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[22] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[23] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[24] -1	0	0x00000400 - 0x0000040f (0x10) IX[B]
	[25] -1	0	0x0000fa00 - 0x0000fa0f (0x10) IX[B]
	[26] -1	0	0x0000fb00 - 0x0000fb03 (0x4) IX[B]
	[27] -1	0	0x0000fc00 - 0x0000fc07 (0x8) IX[B]
	[28] -1	0	0x0000fd00 - 0x0000fd03 (0x4) IX[B]
	[29] -1	0	0x0000fe00 - 0x0000fe07 (0x8) IX[B]
	[30] -1	0	0x0000ef00 - 0x0000efff (0x100) IX[B](B)
(II) Inactive PCI resource ranges:
	[0] -1	0	0x00004100 - 0x000040ff (0x0) IX[B]O
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xfdcfc000 - 0xfdcfc7ff (0x800) MX[B]
	[1] -1	0	0xfdcfd000 - 0xfdcfd0ff (0x100) MX[B]
	[2] -1	0	0xfdce0000 - 0xfdceffff (0x10000) MX[B]
	[3] -1	0	0xfdcfe000 - 0xfdcfefff (0x1000) MX[B]
	[4] -1	0	0xfdcff000 - 0xfdcff0ff (0x100) MX[B]
	[5] -1	0	0xfe02a000 - 0xfe02a0ff (0x100) MX[B]
	[6] -1	0	0xfe02b000 - 0xfe02b3ff (0x400) MX[B]
	[7] -1	0	0xfe02c000 - 0xfe02cfff (0x1000) MX[B]
	[8] -1	0	0xfe02d000 - 0xfe02dfff (0x1000) MX[B]
	[9] -1	0	0xfe02e000 - 0xfe02efff (0x1000) MX[B]
	[10] -1	0	0xfe02f000 - 0xfe02f1ff (0x200) MX[B]
	[11] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[12] -1	0	0xfddf0000 - 0xfddfffff (0x10000) MX[B](B)
	[13] -1	0	0xd8000000 - 0xdfffffff (0x8000000) MX[B](B)
	[14] -1	0	0x0000db00 - 0x0000db7f (0x80) IX[B]
	[15] -1	0	0x0000dc00 - 0x0000dcff (0x100) IX[B]
	[16] -1	0	0x0000dd00 - 0x0000dd1f (0x20) IX[B]
	[17] -1	0	0x0000de00 - 0x0000deff (0x100) IX[B]
	[18] -1	0	0x0000df00 - 0x0000df07 (0x8) IX[B]
	[19] -1	0	0x0000f800 - 0x0000f80f (0x10) IX[B]
	[20] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[21] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[22] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[23] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[24] -1	0	0x00000400 - 0x0000040f (0x10) IX[B]
	[25] -1	0	0x0000fa00 - 0x0000fa0f (0x10) IX[B]
	[26] -1	0	0x0000fb00 - 0x0000fb03 (0x4) IX[B]
	[27] -1	0	0x0000fc00 - 0x0000fc07 (0x8) IX[B]
	[28] -1	0	0x0000fd00 - 0x0000fd03 (0x4) IX[B]
	[29] -1	0	0x0000fe00 - 0x0000fe07 (0x8) IX[B]
	[30] -1	0	0x0000ef00 - 0x0000efff (0x100) IX[B](B)
(II) Inactive PCI resource ranges after removing overlaps:
	[0] -1	0	0x00004100 - 0x000040ff (0x0) IX[B]O
(II) OS-reported resource ranges after removing overlaps with PCI:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) All system resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xfdcfc000 - 0xfdcfc7ff (0x800) MX[B]
	[5] -1	0	0xfdcfd000 - 0xfdcfd0ff (0x100) MX[B]
	[6] -1	0	0xfdce0000 - 0xfdceffff (0x10000) MX[B]
	[7] -1	0	0xfdcfe000 - 0xfdcfefff (0x1000) MX[B]
	[8] -1	0	0xfdcff000 - 0xfdcff0ff (0x100) MX[B]
	[9] -1	0	0xfe02a000 - 0xfe02a0ff (0x100) MX[B]
	[10] -1	0	0xfe02b000 - 0xfe02b3ff (0x400) MX[B]
	[11] -1	0	0xfe02c000 - 0xfe02cfff (0x1000) MX[B]
	[12] -1	0	0xfe02d000 - 0xfe02dfff (0x1000) MX[B]
	[13] -1	0	0xfe02e000 - 0xfe02efff (0x1000) MX[B]
	[14] -1	0	0xfe02f000 - 0xfe02f1ff (0x200) MX[B]
	[15] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[16] -1	0	0xfddf0000 - 0xfddfffff (0x10000) MX[B](B)
	[17] -1	0	0xd8000000 - 0xdfffffff (0x8000000) MX[B](B)
	[18] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[19] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[20] -1	0	0x0000db00 - 0x0000db7f (0x80) IX[B]
	[21] -1	0	0x0000dc00 - 0x0000dcff (0x100) IX[B]
	[22] -1	0	0x0000dd00 - 0x0000dd1f (0x20) IX[B]
	[23] -1	0	0x0000de00 - 0x0000deff (0x100) IX[B]
	[24] -1	0	0x0000df00 - 0x0000df07 (0x8) IX[B]
	[25] -1	0	0x0000f800 - 0x0000f80f (0x10) IX[B]
	[26] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[27] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[28] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[29] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[30] -1	0	0x00000400 - 0x0000040f (0x10) IX[B]
	[31] -1	0	0x0000fa00 - 0x0000fa0f (0x10) IX[B]
	[32] -1	0	0x0000fb00 - 0x0000fb03 (0x4) IX[B]
	[33] -1	0	0x0000fc00 - 0x0000fc07 (0x8) IX[B]
	[34] -1	0	0x0000fd00 - 0x0000fd03 (0x4) IX[B]
	[35] -1	0	0x0000fe00 - 0x0000fe07 (0x8) IX[B]
	[36] -1	0	0x0000ef00 - 0x0000efff (0x100) IX[B](B)
	[37] -1	0	0x00004100 - 0x000040ff (0x0) IX[B]O
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension SHAPE
(II) Loading extension MIT-SUNDRY-NONSTANDARD
(II) Loading extension BIG-REQUESTS
(II) Loading extension SYNC
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XC-MISC
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-Misc
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension TOG-CUP
(II) Loading extension Extended-Visual-Information
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(==) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "freetype"
(II) Loading /usr/lib/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 1.4.0.90, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font FreeType
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension XFree86-DRI
(II) Matched ati from file name ati.ids in autoconfig
(==) Matched ati for the autoconfigured driver
(==) Assigned the driver to the xf86ConfigLayout
(II) LoadModule: "ati"
(II) Loading /usr/lib/xorg/modules/drivers//ati_drv.so
(II) Module ati: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 6.8.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 2.0
(II) LoadModule: "radeon"
(II) Loading /usr/lib/xorg/modules/drivers//radeon_drv.so
(II) Module radeon: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 4.3.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 2.0
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input//mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 1.4.0, module version = 1.2.3
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.0
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input//kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 1.4.0, module version = 1.2.2
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.0
(II) RADEON: Driver for ATI Radeon chipsets:
	ATI Radeon Mobility X600 (M24) 3150 (PCIE),
	ATI Radeon Mobility X300 (M24) 3152 (PCIE),
	ATI FireGL M24 GL 3154 (PCIE), ATI Radeon X600 (RV380) 3E50 (PCIE),
	ATI FireGL V3200 (RV380) 3E54 (PCIE), ATI Radeon IGP320 (A3) 4136,
	ATI Radeon IGP330/340/350 (A4) 4137, ATI Radeon 9500 AD (AGP),
	ATI Radeon 9500 AE (AGP), ATI Radeon 9600TX AF (AGP),
	ATI FireGL Z1 AG (AGP), ATI Radeon 9800SE AH (AGP),
	ATI Radeon 9800 AI (AGP), ATI Radeon 9800 AJ (AGP),
	ATI FireGL X2 AK (AGP), ATI Radeon 9600 AP (AGP),
	ATI Radeon 9600SE AQ (AGP), ATI Radeon 9600XT AR (AGP),
	ATI Radeon 9600 AS (AGP), ATI FireGL T2 AT (AGP), ATI Radeon 9650,
	ATI FireGL RV360 AV (AGP), ATI Radeon 7000 IGP (A4+) 4237,
	ATI Radeon 8500 AIW BB (AGP), ATI Radeon 8500 AIW BC (AGP),
	ATI Radeon IGP320M (U1) 4336, ATI Radeon IGP330M/340M/350M (U2) 4337,
	ATI Radeon Mobility 7000 IGP 4437, ATI Radeon 9000/PRO If (AGP/PCI),
	ATI Radeon 9000 Ig (AGP/PCI), ATI Radeon X800 (R420) JH (AGP),
	ATI Radeon X800PRO (R420) JI (AGP),
	ATI Radeon X800SE (R420) JJ (AGP), ATI Radeon X800 (R420) JK (AGP),
	ATI Radeon X800 (R420) JL (AGP), ATI FireGL X3 (R420) JM (AGP),
	ATI Radeon Mobility 9800 (M18) JN (AGP),
	ATI Radeon X800 SE (R420) (AGP), ATI Radeon X800XT (R420) JP (AGP),
	ATI Radeon X850 XT (R480) (AGP), ATI Radeon X850 SE (R480) (AGP),
	ATI Radeon X850 PRO (R480) (AGP), ATI Radeon X850 XT PE (R480) (AGP),
	ATI Radeon Mobility M7 LW (AGP),
	ATI Mobility FireGL 7800 M7 LX (AGP),
	ATI Radeon Mobility M6 LY (AGP), ATI Radeon Mobility M6 LZ (AGP),
	ATI FireGL Mobility 9000 (M9) Ld (AGP),
	ATI Radeon Mobility 9000 (M9) Lf (AGP),
	ATI Radeon Mobility 9000 (M9) Lg (AGP), ATI Radeon 9700 Pro ND (AGP),
	ATI Radeon 9700/9500Pro NE (AGP), ATI Radeon 9600TX NF (AGP),
	ATI FireGL X1 NG (AGP), ATI Radeon 9800PRO NH (AGP),
	ATI Radeon 9800 NI (AGP), ATI FireGL X2 NK (AGP),
	ATI Radeon 9800XT NJ (AGP),
	ATI Radeon Mobility 9600/9700 (M10/M11) NP (AGP),
	ATI Radeon Mobility 9600 (M10) NQ (AGP),
	ATI Radeon Mobility 9600 (M11) NR (AGP),
	ATI Radeon Mobility 9600 (M10) NS (AGP),
	ATI FireGL Mobility T2 (M10) NT (AGP),
	ATI FireGL Mobility T2e (M11) NV (AGP), ATI Radeon QD (AGP),
	ATI Radeon QE (AGP), ATI Radeon QF (AGP), ATI Radeon QG (AGP),
	ATI FireGL 8700/8800 QH (AGP), ATI Radeon 8500 QL (AGP),
	ATI Radeon 9100 QM (AGP), ATI Radeon 7500 QW (AGP/PCI),
	ATI Radeon 7500 QX (AGP/PCI), ATI Radeon VE/7000 QY (AGP/PCI),
	ATI Radeon VE/7000 QZ (AGP/PCI), ATI ES1000 515E (PCI),
	ATI Radeon Mobility X300 (M22) 5460 (PCIE),
	ATI Radeon Mobility X600 SE (M24C) 5462 (PCIE),
	ATI FireGL M22 GL 5464 (PCIE), ATI Radeon X800 (R423) UH (PCIE),
	ATI Radeon X800PRO (R423) UI (PCIE),
	ATI Radeon X800LE (R423) UJ (PCIE),
	ATI Radeon X800SE (R423) UK (PCIE),
	ATI Radeon X800 XTP (R430) (PCIE), ATI Radeon X800 XL (R430) (PCIE),
	ATI Radeon X800 SE (R430) (PCIE), ATI Radeon X800 (R430) (PCIE),
	ATI FireGL V7100 (R423) (PCIE), ATI FireGL V5100 (R423) UQ (PCIE),
	ATI FireGL unknown (R423) UR (PCIE),
	ATI FireGL unknown (R423) UT (PCIE),
	ATI Mobility FireGL V5000 (M26) (PCIE),
	ATI Mobility FireGL V5000 (M26) (PCIE),
	ATI Mobility Radeon X700 XL (M26) (PCIE),
	ATI Mobility Radeon X700 (M26) (PCIE),
	ATI Mobility Radeon X700 (M26) (PCIE), ATI Radeon 9100 IGP (A5) 5834,
	ATI Radeon Mobility 9100 IGP (U3) 5835,
	ATI Radeon XPRESS 200 5954 (PCIE),
	ATI Radeon XPRESS 200M 5955 (PCIE), ATI Radeon 9250 5960 (AGP),
	ATI Radeon 9200 5961 (AGP), ATI Radeon 9200 5962 (AGP),
	ATI Radeon 9200SE 5964 (AGP), ATI FireMV 2200 (PCI),
	ATI ES1000 5969 (PCI), ATI Radeon XPRESS 200 5974 (PCIE),
	ATI Radeon XPRESS 200M 5975 (PCIE),
	ATI Radeon XPRESS 200 5A41 (PCIE),
	ATI Radeon XPRESS 200M 5A42 (PCIE),
	ATI Radeon XPRESS 200 5A61 (PCIE),
	ATI Radeon XPRESS 200M 5A62 (PCIE),
	ATI Radeon X300 (RV370) 5B60 (PCIE),
	ATI Radeon X600 (RV370) 5B62 (PCIE),
	ATI Radeon X550 (RV370) 5B63 (PCIE),
	ATI Radeon X550XTX (RV370) 5657 (PCIE),
	ATI FireGL V3100 (RV370) 5B64 (PCIE),
	ATI FireMV 2200 PCIE (RV370) 5B65 (PCIE),
	ATI Radeon Mobility 9200 (M9+) 5C61 (AGP),
	ATI Radeon Mobility 9200 (M9+) 5C63 (AGP),
	ATI Mobility Radeon X800 XT (M28) (PCIE),
	ATI Mobility FireGL V5100 (M28) (PCIE),
	ATI Mobility Radeon X800 (M28) (PCIE), ATI Radeon X850 5D4C (PCIE),
	ATI Radeon X850 XT PE (R480) (PCIE),
	ATI Radeon X850 SE (R480) (PCIE), ATI Radeon X850 PRO (R480) (PCIE),
	ATI unknown Radeon / FireGL (R480) 5D50 (PCIE),
	ATI Radeon X850 XT (R480) (PCIE),
	ATI Radeon X800XT (R423) 5D57 (PCIE),
	ATI FireGL V5000 (RV410) (PCIE), ATI Radeon X700 XT (RV410) (PCIE),
	ATI Radeon X700 PRO (RV410) (PCIE),
	ATI Radeon X700 SE (RV410) (PCIE), ATI Radeon X700 (RV410) (PCIE),
	ATI Radeon X700 SE (RV410) (PCIE), ATI Radeon X1800,
	ATI Mobility Radeon X1800 XT, ATI Mobility Radeon X1800,
	ATI Mobility FireGL V7200, ATI FireGL V7200, ATI FireGL V5300,
	ATI Mobility FireGL V7100, ATI Radeon X1800, ATI Radeon X1800,
	ATI Radeon X1800, ATI Radeon X1800, ATI Radeon X1800,
	ATI FireGL V7300, ATI FireGL V7350, ATI Radeon X1600, ATI RV505,
	ATI Radeon X1300/X1550, ATI Radeon X1550, ATI M54-GL,
	ATI Mobility Radeon X1400, ATI Radeon X1300/X1550,
	ATI Radeon X1550 64-bit, ATI Mobility Radeon X1300,
	ATI Mobility Radeon X1300, ATI Mobility Radeon X1300,
	ATI Mobility Radeon X1300, ATI Radeon X1300, ATI Radeon X1300,
	ATI RV505, ATI RV505, ATI FireGL V3300, ATI FireGL V3350,
	ATI Radeon X1300, ATI Radeon X1550 64-bit, ATI Radeon X1300/X1550,
	ATI Radeon X1600, ATI Radeon X1300/X1550, ATI Mobility Radeon X1450,
	ATI Radeon X1300/X1550, ATI Mobility Radeon X2300,
	ATI Mobility Radeon X2300, ATI Mobility Radeon X1350,
	ATI Mobility Radeon X1350, ATI Mobility Radeon X1450,
	ATI Radeon X1300, ATI Radeon X1550, ATI Mobility Radeon X1350,
	ATI FireMV 2250, ATI Radeon X1550 64-bit, ATI Radeon X1600,
	ATI Radeon X1650, ATI Radeon X1600, ATI Radeon X1600,
	ATI Mobility FireGL V5200, ATI Mobility Radeon X1600,
	ATI Radeon X1650, ATI Radeon X1650, ATI Radeon X1600,
	ATI Radeon X1300 XT/X1600 Pro, ATI FireGL V3400,
	ATI Mobility FireGL V5250, ATI Mobility Radeon X1700,
	ATI Mobility Radeon X1700 XT, ATI FireGL V5200,
	ATI Mobility Radeon X1700, ATI  Radeon X2300HD,
	ATI Mobility Radeon HD 2300, ATI Mobility Radeon HD 2300,
	ATI Radeon X1950, ATI Radeon X1900, ATI Radeon X1950,
	ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
	ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
	ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
	ATI AMD Stream Processor, ATI Radeon X1900, ATI Radeon X1950,
	ATI RV560, ATI RV560, ATI Mobility Radeon X1900, ATI RV560,
	ATI Radeon X1950 GT, ATI RV570, ATI RV570, ATI ATI FireGL V7400,
	ATI RV560, ATI Radeon X1650, ATI Radeon X1650, ATI RV560,
	ATI Radeon 9100 PRO IGP 7834, ATI Radeon Mobility 9200 IGP 7835,
	ATI Radeon X1200, ATI Radeon X1200, ATI RS740, ATI RS740M, ATI RS740,
	ATI RS740M, ATI Radeon HD 2900 XT, ATI Radeon HD 2900 XT,
	ATI Radeon HD 2900 XT, ATI Radeon HD 2900 Pro, ATI Radeon HD 2900 GT,
	ATI FireGL V8650, ATI FireGL V8600, ATI FireGL V7600, ATI RV610,
	ATI Radeon HD 2400 XT, ATI Radeon HD 2400 Pro,
	ATI ATI Radeon HD 2400 PRO AGP, ATI FireGL V4000, ATI RV610,
	ATI ATI Radeon HD 2350, ATI Mobility Radeon HD 2400 XT,
	ATI Mobility Radeon HD 2400, ATI ATI RADEON E2400, ATI RV610,
	ATI RV670, ATI Radeon HD3870, ATI Radeon HD3850, ATI RV670,
	ATI Radeon HD3870 X2, ATI FireGL V7700, ATI RV630,
	ATI Mobility Radeon HD 2600, ATI Mobility Radeon HD 2600 XT,
	ATI ATI Radeon HD 2600 XT AGP, ATI ATI Radeon HD 2600 Pro AGP,
	ATI Radeon HD 2600 XT, ATI Radeon HD 2600 Pro, ATI Gemini RV630,
	ATI Gemini ATI Mobility Radeon HD 2600 XT, ATI FireGL V5600,
	ATI FireGL V3600, ATI ATI Radeon HD 2600 LE
(II) Primary Device is: PCI 01:05:0
(--) Assigning device section with no busID to primary device
(--) Chipset ATI Radeon XPRESS 200 5954 (PCIE) found
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xfdcfc000 - 0xfdcfc7ff (0x800) MX[B]
	[5] -1	0	0xfdcfd000 - 0xfdcfd0ff (0x100) MX[B]
	[6] -1	0	0xfdce0000 - 0xfdceffff (0x10000) MX[B]
	[7] -1	0	0xfdcfe000 - 0xfdcfefff (0x1000) MX[B]
	[8] -1	0	0xfdcff000 - 0xfdcff0ff (0x100) MX[B]
	[9] -1	0	0xfe02a000 - 0xfe02a0ff (0x100) MX[B]
	[10] -1	0	0xfe02b000 - 0xfe02b3ff (0x400) MX[B]
	[11] -1	0	0xfe02c000 - 0xfe02cfff (0x1000) MX[B]
	[12] -1	0	0xfe02d000 - 0xfe02dfff (0x1000) MX[B]
	[13] -1	0	0xfe02e000 - 0xfe02efff (0x1000) MX[B]
	[14] -1	0	0xfe02f000 - 0xfe02f1ff (0x200) MX[B]
	[15] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[16] -1	0	0xfddf0000 - 0xfddfffff (0x10000) MX[B](B)
	[17] -1	0	0xd8000000 - 0xdfffffff (0x8000000) MX[B](B)
	[18] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[19] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[20] -1	0	0x0000db00 - 0x0000db7f (0x80) IX[B]
	[21] -1	0	0x0000dc00 - 0x0000dcff (0x100) IX[B]
	[22] -1	0	0x0000dd00 - 0x0000dd1f (0x20) IX[B]
	[23] -1	0	0x0000de00 - 0x0000deff (0x100) IX[B]
	[24] -1	0	0x0000df00 - 0x0000df07 (0x8) IX[B]
	[25] -1	0	0x0000f800 - 0x0000f80f (0x10) IX[B]
	[26] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[27] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[28] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[29] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[30] -1	0	0x00000400 - 0x0000040f (0x10) IX[B]
	[31] -1	0	0x0000fa00 - 0x0000fa0f (0x10) IX[B]
	[32] -1	0	0x0000fb00 - 0x0000fb03 (0x4) IX[B]
	[33] -1	0	0x0000fc00 - 0x0000fc07 (0x8) IX[B]
	[34] -1	0	0x0000fd00 - 0x0000fd03 (0x4) IX[B]
	[35] -1	0	0x0000fe00 - 0x0000fe07 (0x8) IX[B]
	[36] -1	0	0x0000ef00 - 0x0000efff (0x100) IX[B](B)
	[37] -1	0	0x00004100 - 0x000040ff (0x0) IX[B]O
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xfdcfc000 - 0xfdcfc7ff (0x800) MX[B]
	[5] -1	0	0xfdcfd000 - 0xfdcfd0ff (0x100) MX[B]
	[6] -1	0	0xfdce0000 - 0xfdceffff (0x10000) MX[B]
	[7] -1	0	0xfdcfe000 - 0xfdcfefff (0x1000) MX[B]
	[8] -1	0	0xfdcff000 - 0xfdcff0ff (0x100) MX[B]
	[9] -1	0	0xfe02a000 - 0xfe02a0ff (0x100) MX[B]
	[10] -1	0	0xfe02b000 - 0xfe02b3ff (0x400) MX[B]
	[11] -1	0	0xfe02c000 - 0xfe02cfff (0x1000) MX[B]
	[12] -1	0	0xfe02d000 - 0xfe02dfff (0x1000) MX[B]
	[13] -1	0	0xfe02e000 - 0xfe02efff (0x1000) MX[B]
	[14] -1	0	0xfe02f000 - 0xfe02f1ff (0x200) MX[B]
	[15] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[16] -1	0	0xfddf0000 - 0xfddfffff (0x10000) MX[B](B)
	[17] -1	0	0xd8000000 - 0xdfffffff (0x8000000) MX[B](B)
	[18] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[19] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[20] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[21] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[22] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[23] -1	0	0x0000db00 - 0x0000db7f (0x80) IX[B]
	[24] -1	0	0x0000dc00 - 0x0000dcff (0x100) IX[B]
	[25] -1	0	0x0000dd00 - 0x0000dd1f (0x20) IX[B]
	[26] -1	0	0x0000de00 - 0x0000deff (0x100) IX[B]
	[27] -1	0	0x0000df00 - 0x0000df07 (0x8) IX[B]
	[28] -1	0	0x0000f800 - 0x0000f80f (0x10) IX[B]
	[29] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[30] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[31] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[32] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[33] -1	0	0x00000400 - 0x0000040f (0x10) IX[B]
	[34] -1	0	0x0000fa00 - 0x0000fa0f (0x10) IX[B]
	[35] -1	0	0x0000fb00 - 0x0000fb03 (0x4) IX[B]
	[36] -1	0	0x0000fc00 - 0x0000fc07 (0x8) IX[B]
	[37] -1	0	0x0000fd00 - 0x0000fd03 (0x4) IX[B]
	[38] -1	0	0x0000fe00 - 0x0000fe07 (0x8) IX[B]
	[39] -1	0	0x0000ef00 - 0x0000efff (0x100) IX[B](B)
	[40] -1	0	0x00004100 - 0x000040ff (0x0) IX[B]O
	[41] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[42] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) RADEON(0): MMIO registers at 0x00000000fddf0000: size 64KB
(II) RADEON(0): PCI bus 1 card 5 func 0
(II) RADEON(0): Creating default Display subsection in Screen section
	"Default Screen" for depth/fbbpp 24/32
(==) RADEON(0): Depth 24, (==) framebuffer bpp 32
(II) RADEON(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
(==) RADEON(0): Default visual is TrueColor
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 0.1.0
	ABI class: X.Org Video Driver, version 2.0
(II) RADEON(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(==) RADEON(0): RGB weight 888
(II) RADEON(0): Using 8 bits per RGB (8 bit DAC)
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Video Driver, version 2.0
(II) RADEON(0): initializing int10
(II) RADEON(0): Primary V_BIOS segment is: 0xc000
(--) RADEON(0): Chipset: "ATI Radeon XPRESS 200 5954 (PCIE)" (ChipID = 0x5954)
(--) RADEON(0): Linear framebuffer at 0x00000000d8000000
(II) RADEON(0): PCI card detected
(II) RADEON(0): Legacy BIOS detected
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenByBusid: Searching for BusID pci:0000:01:05.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenByBusid: drmOpenMinor returns 7
drmOpenByBusid: drmGetBusid reports pci:0000:01:05.0
(II) RADEON(0): [dri] Found DRI library version 1.3.0 and kernel module version 1.28.0
(II) RADEON(0): Direct rendering experimental on RS400/Xpress 200 enabled
(==) RADEON(0): Page Flipping disabled
(II) RADEON(0): Will try to use DMA for Xv image transfers
(II) RADEON(0): Detected total video RAM=65536K, accessible=131072K (PCI BAR=131072K)
(--) RADEON(0): Mapped VideoRAM: 65536 kByte (64 bit DDR SDRAM)
(II) RADEON(0): Color tiling enabled by default
(II) RADEON(0): Max desktop size set to 2560x1200
(II) RADEON(0): For a larger or smaller max desktop size, add a Virtual line to your xorg.conf
(II) RADEON(0): If you are having trouble with 3D, reduce the desktop size by adjusting the Virtual line to your xorg.conf
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"(II) Module "ddc" already built-in
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"(II) Module "i2c" already built-in
(II) RADEON(0): ref_freq: 1432, min_out_pll: 20000, max_out_pll: 40000, min_in_pll: 100, max_in_pll: 1350, xclk: 20500, sclk: 205.000000, mclk: 300.000000
(II) RADEON(0): PLL parameters: rf=1432 rd=6 min=20000 max=40000 said:**
> http://gatos.sf.net[/url].
(!!) RADEON(0): MergedFB support has been removed and replaced with xrandr 1.2 support
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0xfddf0000 - 0xfddfffff (0x10000) MX[B]
	[1] 0	0	0xd8000000 - 0xdfffffff (0x8000000) MX[B]
	[2] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[3] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[4] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[5] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[6] -1	0	0xfdcfc000 - 0xfdcfc7ff (0x800) MX[B]
	[7] -1	0	0xfdcfd000 - 0xfdcfd0ff (0x100) MX[B]
	[8] -1	0	0xfdce0000 - 0xfdceffff (0x10000) MX[B]
	[9] -1	0	0xfdcfe000 - 0xfdcfefff (0x1000) MX[B]
	[10] -1	0	0xfdcff000 - 0xfdcff0ff (0x100) MX[B]
	[11] -1	0	0xfe02a000 - 0xfe02a0ff (0x100) MX[B]
	[12] -1	0	0xfe02b000 - 0xfe02b3ff (0x400) MX[B]
	[13] -1	0	0xfe02c000 - 0xfe02cfff (0x1000) MX[B]
	[14] -1	0	0xfe02d000 - 0xfe02dfff (0x1000) MX[B]
	[15] -1	0	0xfe02e000 - 0xfe02efff (0x1000) MX[B]
	[16] -1	0	0xfe02f000 - 0xfe02f1ff (0x200) MX[B]
	[17] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[18] -1	0	0xfddf0000 - 0xfddfffff (0x10000) MX[B](B)
	[19] -1	0	0xd8000000 - 0xdfffffff (0x8000000) MX[B](B)
	[20] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprU)
	[21] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprU)
	[22] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprU)
	[23] 0	0	0x0000ef00 - 0x0000efff (0x100) IX[B]
	[24] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[25] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[26] -1	0	0x0000db00 - 0x0000db7f (0x80) IX[B]
	[27] -1	0	0x0000dc00 - 0x0000dcff (0x100) IX[B]
	[28] -1	0	0x0000dd00 - 0x0000dd1f (0x20) IX[B]
	[29] -1	0	0x0000de00 - 0x0000deff (0x100) IX[B]
	[30] -1	0	0x0000df00 - 0x0000df07 (0x8) IX[B]
	[31] -1	0	0x0000f800 - 0x0000f80f (0x10) IX[B]
	[32] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[33] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[34] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[35] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[36] -1	0	0x00000400 - 0x0000040f (0x10) IX[B]
	[37] -1	0	0x0000fa00 - 0x0000fa0f (0x10) IX[B]
	[38] -1	0	0x0000fb00 - 0x0000fb03 (0x4) IX[B]
	[39] -1	0	0x0000fc00 - 0x0000fc07 (0x8) IX[B]
	[40] -1	0	0x0000fd00 - 0x0000fd03 (0x4) IX[B]
	[41] -1	0	0x0000fe00 - 0x0000fe07 (0x8) IX[B]
	[42] -1	0	0x0000ef00 - 0x0000efff (0x100) IX[B](B)
	[43] -1	0	0x00004100 - 0x000040ff (0x0) IX[B]O
	[44] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[45] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) RADEON(0): RADEONScreenInit d8000000 0 0
(==) RADEON(0): Write-combining range (0xd8000000,0x4000000)
(WW) RADEON(0): Cannot read colourmap from VGA.  Will restore with default
Entering TV Save
Save TV timing tables
saveTimingTables: reading timing tables
TV Save done
disable montype: 1
(==) RADEON(0): Using 24 bit depth buffer
(II) RADEON(0): RADEONInitMemoryMap() : 
(II) RADEON(0):   mem_size         : 0x04000000
(II) RADEON(0):   MC_FB_LOCATION   : 0x0fff0c00
(II) RADEON(0):   MC_AGP_LOCATION  : 0xffffffc0
(II) RADEON(0): Depth moves disabled by default
(II) RADEON(0): CP in BM mode
(II) RADEON(0): Using 8 MB GART aperture
(II) RADEON(0): Using 1 MB for the ring buffer
(II) RADEON(0): Using 2 MB for vertex/indirect buffers
(II) RADEON(0): Using 5 MB for GART textures
(II) RADEON(0): Memory manager initialized to (0,0) (1280,8191)
(II) RADEON(0): Reserved area from (0,1200) to (1280,1202)
(II) RADEON(0): Largest offscreen area available: 1280 x 6989
(II) RADEON(0): Will use front buffer at offset 0x0
(II) RADEON(0): Will use back buffer at offset 0x1248000
(II) RADEON(0): Will use depth buffer at offset 0x1824000
(II) RADEON(0): Will use 34816 kb for textures at offset 0x1e00000
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenByBusid: Searching for BusID pci:0000:01:05.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenByBusid: drmOpenMinor returns 7
drmOpenByBusid: drmGetBusid reports pci:0000:01:05.0
(II) [drm] DRM interface version 1.3
(II) [drm] DRM open master succeeded.
(II) RADEON(0): [drm] Using the DRM lock SAREA also for drawables.
(II) RADEON(0): [drm] framebuffer handle = 0xd8000000
(II) RADEON(0): [drm] added 1 reserved context for kernel
(II) RADEON(0): X context handle = 0x1
(II) RADEON(0): [drm] installed DRM signal handler
(II) RADEON(0): [pci] 8192 kB allocated with handle 0x00000000
(II) RADEON(0): [pci] ring handle = 0xccc51000
(II) RADEON(0): [pci] Ring mapped at 0xb7960000
(II) RADEON(0): [pci] Ring contents 0x00000000
(II) RADEON(0): [pci] ring read ptr handle = 0xccd52000
(II) RADEON(0): [pci] Ring read ptr mapped at 0xb795f000
(II) RADEON(0): [pci] Ring read ptr contents 0x00000000
(II) RADEON(0): [pci] vertex/indirect buffers handle = 0xccd53000
(II) RADEON(0): [pci] Vertex/indirect buffers mapped at 0xb369d000
(II) RADEON(0): [pci] Vertex/indirect buffers contents 0x00000000
(II) RADEON(0): [pci] GART texture map handle = 0xccf53000
(II) RADEON(0): [pci] GART Texture map mapped at 0xb31bd000
(II) RADEON(0): [drm] register handle = 0xfddf0000
(II) RADEON(0): [dri] Visual configs initialized
disable montype: 1
init memmap
init common
init crtc1
init pll1
freq: 80140000
best_freq: 80136923
best_feedback_div: 291
best_ref_div: 13
best_post_div: 4
restore memmap
(II) RADEON(0): RADEONRestoreMemMapRegisters() : 
(II) RADEON(0):   MC_FB_LOCATION   : 0x0fff0c00 0x0fff0c00
(II) RADEON(0):   MC_AGP_LOCATION  : 0xffffffc0
restore common
restore crtc1
restore pll1
finished PLL1
restore dac
enable montype: 1
(WW) RADEON(0): No crtc mode list for crtc 1,continuing with desired mode
disable montype: 1
(==) RADEON(0): Backing store disabled
(II) RADEON(0): [DRI] installation complete
(II) RADEON(0): [drm] Added 32 65536 byte vertex/indirect buffers
(II) RADEON(0): [drm] Mapped 32 vertex/indirect buffers
(II) RADEON(0): [drm] dma control initialized, using IRQ 20
(II) RADEON(0): [drm] Initialized kernel GART heap manager, 5111808
(WW) RADEON(0): DRI init changed memory map, adjusting ...
(WW) RADEON(0):   MC_FB_LOCATION  was: 0x0fff0c00 is: 0x0fff0c00
(WW) RADEON(0):   MC_AGP_LOCATION was: 0xffffffc0 is: 0x11ff1000
(II) RADEON(0): RADEONRestoreMemMapRegisters() : 
(II) RADEON(0):   MC_FB_LOCATION   : 0x0fff0c00 0x0fff0c00
(II) RADEON(0):   MC_AGP_LOCATION  : 0x11ff1000
(II) RADEON(0): Direct rendering enabled
(II) RADEON(0): Render acceleration unsupported on Radeon 9500/9700 and newer.
(II) RADEON(0): Render acceleration disabled
(II) RADEON(0): Using XFree86 Acceleration Architecture (XAA)
	Screen to screen bit blits
	Solid filled rectangles
	8x8 mono pattern filled rectangles
	Indirect CPU to Screen color expansion
	Solid Lines
	Scanline Image Writes
	Setting up tile and stipple cache:
		32 128x128 slots
		32 256x256 slots
		16 512x512 slots
(II) RADEON(0): Acceleration enabled
(II) RADEON(0): DPMS enabled
(==) RADEON(0): Silken mouse enabled
(II) RADEON(0): Using hardware cursor 0 (scanline 1202)
(II) RADEON(0): Using hardware cursor 1 (scanline 1205)
(II) RADEON(0): Largest offscreen area available: 1280 x 6982
(II) RADEON(0): No video input capabilities detected and no information is provided - disabling multimedia i2c
(II) Loading sub module "theatre_detect"
(II) LoadModule: "theatre_detect"
(II) Loading /usr/lib/xorg/modules/multimedia//theatre_detect_drv.so
(II) Module theatre_detect: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Video Driver, version 2.0
(II) RADEON(0): no multimedia table present, disabling Rage Theatre.
(II) RADEON(0): RandR 1.2 enabled, ignore the following RandR disabled message.
(--) RandR disabled
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension XAccessControlExtension
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension XFree86-Bigfont
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 8, (OK)
drmOpenByBusid: Searching for BusID pci:0000:01:05.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 8, (OK)
drmOpenByBusid: drmOpenMinor returns 8
drmOpenByBusid: drmGetBusid reports pci:0000:01:05.0
(WW) AIGLX: 3D driver claims to not support visual 0x23
(WW) AIGLX: 3D driver claims to not support visual 0x24
(WW) AIGLX: 3D driver claims to not support visual 0x25
(WW) AIGLX: 3D driver claims to not support visual 0x26
(WW) AIGLX: 3D driver claims to not support visual 0x27
(WW) AIGLX: 3D driver claims to not support visual 0x28
(WW) AIGLX: 3D driver claims to not support visual 0x29
(WW) AIGLX: 3D driver claims to not support visual 0x2a
(WW) AIGLX: 3D driver claims to not support visual 0x2b
(WW) AIGLX: 3D driver claims to not support visual 0x2c
(WW) AIGLX: 3D driver claims to not support visual 0x2d
(WW) AIGLX: 3D driver claims to not support visual 0x2e
(WW) AIGLX: 3D driver claims to not support visual 0x2f
(WW) AIGLX: 3D driver claims to not support visual 0x30
(WW) AIGLX: 3D driver claims to not support visual 0x31
(WW) AIGLX: 3D driver claims to not support visual 0x32
(II) AIGLX: Loaded and initialized /usr/lib/dri/r300_dri.so
(II) GLX: Initialized DRI GL provider for screen 0
(II) RADEON(0): Setting screen physical size to 338 x 203
(WW) Configured Mouse: No Device specified, looking for one...
(II) Configured Mouse: Setting Device option to "/dev/input/mice"
(--) Configured Mouse: Device: "/dev/input/mice"
(==) Configured Mouse: Protocol: "Auto"
(**) Option "CorePointer"
(**) Configured Mouse: always reports core events
(**) Option "Device" "/dev/input/mice"
(==) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 9
(**) Configured Mouse: Sensitivity: 1
(**) Option "CoreKeyboard"
(**) Generic Keyboard: always reports core events
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc105"
(**) Generic Keyboard: XkbModel: "pc105"
(**) Option "XkbLayout" "gb"
(**) Generic Keyboard: XkbLayout: "gb"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(II) evaluating device (Generic Keyboard)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(II) evaluating device (Configured Mouse)
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(--) Configured Mouse: PnP-detected protocol: "ExplorerPS/2"
(II) Configured Mouse: ps2EnableDataReporting: succeeded
enable montype: 1
(II) RADEON(0): I2C device "VGA-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "VGA-0:ddc2" removed.
(II) RADEON(0): I2C device "VGA-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "VGA-0:ddc2" removed.
(II) RADEON(0): I2C device "VGA-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "VGA-0:ddc2" removed.
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 0
(II) RADEON(0): I2C device "VGA-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "VGA-0:ddc2" removed.
(II) RADEON(0): I2C device "VGA-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "VGA-0:ddc2" removed.
(II) RADEON(0): I2C device "VGA-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "VGA-0:ddc2" removed.
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 0
(II) RADEON(0): I2C device "VGA-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "VGA-0:ddc2" removed.
(II) RADEON(0): I2C device "VGA-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "VGA-0:ddc2" removed.
(II) RADEON(0): I2C device "VGA-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "VGA-0:ddc2" removed.
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 0
(II) RADEON(0): I2C device "VGA-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "VGA-0:ddc2" removed.
(II) RADEON(0): I2C device "VGA-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "VGA-0:ddc2" removed.
(II) RADEON(0): I2C device "VGA-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "VGA-0:ddc2" removed.
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 0
(II) RADEON(0): I2C device "VGA-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "VGA-0:ddc2" removed.
(II) RADEON(0): I2C device "VGA-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "VGA-0:ddc2" removed.
(II) RADEON(0): I2C device "VGA-0:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "VGA-0:ddc2" removed.
(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 0
[/noparse]

Sorry for the delayed reply - thought I'd try a reinstall, that failed to fix it too so its bound to be some sort of hardware issue, right?

---

### Post by Zorael on 2008-05-10
Could this be X trying to display content at resolutions or refresh rates your monitor doesn't support? The version in 8.04 auto-detects a whole lot more than it did in earlier versions, so perhaps it's just a tad too daring.

The easy way would be to limit available modes in /etc/X11/xorg.conf and see if that helped.

Off the top of my head:
```
Section "Device"
	Identifier	"Configured Video Card"
	Driver		"ati"  # or "radeon", or "vesa", heck if I know what's best for your system. Your Xorg.0.log suggests it's a radeon card though, but may want to try ati or vesa too, for troubleshooting purposes.
EndSection

Section "Screen"
	Identifier 	"Default Screen"
	Device		"Configured Video Card"
	Monitor		"Configured Monitor"
	DefaultDepth	24
	SubSection "Display"
		Modes	"1280x1024@60" "1024x768@60" "800x600@60" "640x480@60"  # obviously, change resolutions and @refresh rates as you please, but set them low to begin with. First entry will be the default (read: at login), even if lower than the following resolutions
	EndSubSection
EndSection
```

---

### Post by pootsey on 2008-05-10
Okay, I'm there but I have a problem...cant save the file as only root has access to do so (and I cant login as root obviously) :(

*noob*

---

### Post by Zorael on 2008-05-10
```
$ sudo nano /etc/X11/xorg.conf
```
:>

Or boot up in recovery mode and just drop to a root shell.

---

### Post by pootsey on 2008-05-10
How bizarre, first time I did it, it still didn't work on radeon, ati or vesa...I tried fiddling with the resolutions aswell.

Then I must of bodged the file up because it booted into low gfx and prompted me to manually choose my resolution etc..

I chose the same settings as my other Windows box uses and my monitor displays a "Cannot Display this mode" warning...I also selected the monitor model name from the drop down box for ideal settings and it still popped up with this message.

Any ideas?

---

