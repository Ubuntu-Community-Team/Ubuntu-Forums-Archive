---
title: "Impossible to boot - boot-repair utility failed"
date: 2014-04-12
forum: General Help
---

### Post by mths2 on 2014-04-12
Hello everyone,

While normally using my computer, everything suddenly froze. I found no other solution than manually restarting, and then, it had become impossible to boot. After some hours of searching, I burnt the Live CD, started Ubuntu from the CD, and used the boot-repair utility. I got an error at the end of its execution and the following log :

```
[TABLE="class: pastetable"]
[TR]
[TD="class: linenos"] 1
   2
   3
   4
   5
   6
   7
   8
   9
  10
  11
  12
  13
  14
  15
  16
  17
  18
  19
  20
  21
  22
  23
  24
  25
  26
  27
  28
  29
  30
  31
  32
  33
  34
  35
  36
  37
  38
  39
  40
  41
  42
  43
  44
  45
  46
  47
  48
  49
  50
  51
  52
  53
  54
  55
  56
  57
  58
  59
  60
  61
  62
  63
  64
  65
  66
  67
  68
  69
  70
  71
  72
  73
  74
  75
  76
  77
  78
  79
  80
  81
  82
  83
  84
  85
  86
  87
  88
  89
  90
  91
  92
  93
  94
  95
  96
  97
  98
  99
 100
 101
 102
 103
 104
 105
 106
 107
 108
 109
 110
 111
 112
 113
 114
 115
 116
 117
 118
 119
 120
 121
 122
 123
 124
 125
 126
 127
 128
 129
 130
 131
 132
 133
 134
 135
 136
 137
 138
 139
 140
 141
 142
 143
 144
 145
 146
 147
 148
 149
 150
 151
 152
 153
 154
 155
 156
 157
 158
 159
 160
 161
 162
 163
 164
 165
 166
 167
 168
 169
 170
 171
 172
 173
 174
 175
 176
 177
 178
 179
 180
 181
 182
 183
 184
 185
 186
 187
 188
 189
 190
 191
 192
 193
 194
 195
 196
 197
 198
 199
 200
 201
 202
 203
 204
 205
 206
 207
 208
 209
 210
 211
 212
 213
 214
 215
 216
 217
 218
 219
 220
 221
 222
 223
 224
 225
 226
 227
 228
 229
 230
 231
 232
 233
 234
 235
 236
 237
 238
 239
 240
 241
 242
 243
 244
 245
 246
 247
 248
 249
 250
 251
 252
 253
 254
 255
 256
 257
 258
 259
 260
 261
 262
 263
 264
 265
 266
 267
 268
 269
 270
 271
 272
 273
 274
 275
 276
 277
 278
 279
 280
 281
 282
 283
 284
 285
 286
 287
 288
 289
 290
 291
 292
 293
 294
 295
 296
 297
 298
 299
 300
 301
 302
 303
 304
 305
 306
 307
 308
 309
 310
 311
 312
 313
 314
 315
 316
 317
 318
 319
 320
 321
 322
 323
 324
 325
 326
 327
 328
 329
 330
 331
 332
 333
 334
 335
 336
 337
 338
 339
 340
 341
 342
 343
 344
 345
 346
 347
 348
 349
 350
 351
 352
 353
 354
 355
 356
 357
 358
 359
 360
 361
 362
 363
 364
 365
 366
 367
 368
 369
 370
 371
 372
 373
 374
 375
 376
 377
 378
 379
 380
 381
 382
 383
 384
 385
 386
 387
 388
 389
 390
 391
 392
 393
 394
 395
 396
 397
 398
 399
 400
 401
 402
 403
 404
 405
 406
 407
 408
 409
 410
 411
 412
 413
 414
 415
 416
 417
 418
 419
 420
 421
 422
 423
 424
 425
 426
 427
 428
 429
 430
 431
 432
 433
 434
 435
 436
 437
 438
 439
 440
 441
 442
 443
 444
 445
 446
 447
 448
 449
 450
 451
 452
 453
 454
 455
 456
 457
 458
 459
 460
 461
 462
 463
 464
 465
 466
 467
 468
 469
 470
 471
 472
 473
 474
 475
 476
 477
 478
 479
 480
 481
 482
 483
 484
 485
 486
 487
 488
 489
 490
 491
 492
 493
 494
 495
 496
 497
 498
 499
 500
 501
 502
 503
 504
 505
 506
 507
 508
 509
 510
 511
 512
 513
 514
 515
 516
 517
 518
 519
 520
 521
 522
 523
 524
 525
 526
 527
 528
 529
 530
 531
 532
 533
 534
 535
 536
 537
 538
 539
 540
 541
 542
 543
 544
 545
 546
 547
 548
 549
 550
 551
 552
 553
 554
 555
 556
 557
 558
 559
 560
 561
 562
 563
 564
 565
 566
 567
 568
 569
 570
 571
 572
 573
 574
 575
 576
 577
 578
 579
 580
 581
 582
 583
 584
 585
 586
 587
 588
 589
 590
 591
 592
 593
 594
 595
 596
 597
 598
 599
 600
 601
 602
 603
 604
 605
 606
 607
 608
 609
 610
 611
 612
 613
 614
 615
 616
 617
 618
 619
 620
 621
 622
 623
 624
 625
 626
 627
 628
 629
 630
 631
 632
 633
 634
 635
 636
 637
 638
 639
 640
 641
 642
 643
 644
 645
 646
 647
 648
 649
 650
 651
 652
 653
 654
 655
 656
 657
 658
 659
 660
 661
 662
 663
 664
 665
 666
 667
 668
 669
 670
 671
 672
 673
 674
 675
 676
 677
 678
 679
 680
 681
 682
 683
 684
 685
 686
 687
 688
 689
 690
 691
 692
 693
 694
 695
 696
 697
 698
 699
 700
 701
 702
 703
 704
 705
 706
 707
 708
 709
 710
 711
 712
 713
 714
 715
 716
 717
 718
 719
 720
 721
 722
 723
 724
 725
 726
 727
 728
 729
 730
 731
 732
 733
 734
 735
 736
 737
 738
 739
 740
 741
 742
 743
 744
 745
 746
 747
 748
 749
 750
 751
 752
 753
 754
 755
 756
 757
 758
 759
 760
 761
 762
 763
 764
 765
 766
 767
 768
 769
 770
 771
 772
 773
 774
 775
 776
 777
 778
 779
 780
 781
 782
 783
 784
 785
 786
 787
 788
 789
 790
 791
 792
 793
 794
 795
 796
 797
 798
 799
 800
 801
 802
 803
 804
 805
 806
 807
 808
 809
 810
 811
 812
 813
 814
 815
 816
 817
 818
 819
 820
 821
 822
 823
 824
 825
 826
 827
 828
 829
 830
 831
 832
 833
 834
 835
 836
 837
 838
 839
 840
 841
 842
 843
 844
 845
 846
 847
 848
 849
 850
 851
 852
 853
 854
 855
 856
 857
 858
 859
 860
 861
 862
 863
 864
 865
 866
 867
 868
 869
 870
 871
 872
 873
 874
 875
 876
 877
 878
 879
 880
 881
 882
 883
 884
 885
 886
 887
 888
 889
 890
 891
 892
 893
 894
 895
 896
 897
 898
 899
 900
 901
 902
 903
 904
 905
 906
 907
 908
 909
 910
 911
 912
 913
 914
 915
 916
 917
 918
 919
 920
 921
 922
 923
 924
 925
 926
 927
 928
 929
 930
 931
 932
 933
 934
 935
 936
 937
 938
 939
 940
 941
 942
 943
 944
 945
 946
 947
 948
 949
 950
 951
 952
 953
 954
 955
 956
 957
 958
 959
 960
 961
 962
 963
 964
 965
 966
 967
 968
 969
 970
 971
 972
 973
 974
 975
 976
 977
 978
 979
 980
 981
 982
 983
 984
 985
 986
 987
 988
 989
 990
 991
 992
 993
 994
 995
 996
 997
 998
 999
1000
1001
1002
1003
1004
1005
1006
1007
1008
1009
1010
1011
1012
1013
1014
1015
1016
1017
1018
1019
1020
1021
1022
1023
1024
1025
1026
1027
1028
1029
1030
1031
1032
1033
1034
1035
1036
1037
1038
1039
1040
1041
1042
1043
1044
1045
1046
1047
1048
1049
1050
1051
1052
1053
1054
1055
1056
1057
1058
1059
1060
1061
1062
1063
1064
1065
1066
1067
1068
1069
1070
1071
1072
1073
1074
1075
1076
1077
1078
1079
1080
1081
1082
1083
1084
1085
1086
1087
1088
1089
1090
1091
1092
1093
1094
1095
1096
1097
1098
1099
1100
1101
1102
1103
1104
1105
1106
1107
1108
1109
1110
1111
1112
1113
1114
1115
1116
1117
1118
1119
1120
1121
1122
1123
1124
1125
1126
1127
1128
1129
1130
1131
1132
1133
1134
1135
1136
1137
1138
1139
1140
1141
1142
1143
1144
1145
1146
1147
1148
1149
1150
1151
1152
1153
1154
1155
1156
1157
1158
1159
1160
1161
1162
1163
1164
1165
1166
1167
1168
1169
1170
1171
1172
1173
1174
1175
1176
1177
1178
1179
1180
1181
1182
1183
1184
1185
1186
1187
1188
1189
1190
1191
1192
1193
1194
1195
1196
1197
1198
1199
1200
1201
1202
1203
1204
1205
1206
1207
1208
1209
1210
1211
1212
1213
1214
1215
1216
1217
1218
1219
1220
1221
1222
1223
1224
1225
1226
1227
1228
1229
1230
1231
1232
1233
1234
1235
1236
1237
1238
1239
1240
1241
1242
1243
1244
1245
1246
1247
1248
1249
1250
1251
1252
1253
1254
1255
1256
1257
1258
1259
1260
1261
1262
1263
1264
1265
1266
1267
1268
1269
1270
1271
1272
1273
1274
1275
1276
1277
1278
1279
1280
1281
1282
1283
1284
1285
1286
[/TD]
[TD="class: code"][COLOR=#000000] Boot Info Script e7fc706 + Boot-Repair extra info      [COLOR=#666666][[/COLOR]Boot-Info 23Dec2013[COLOR=#666666]][/COLOR]


[COLOR=#666666]=============================[/COLOR] Boot Info Summary: [COLOR=#666666]===============================[/COLOR]

 [COLOR=#666666]=[/COLOR]> Grub2 [COLOR=#666666]([/COLOR]v1.99[COLOR=#666666])[/COLOR] is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive [COLOR=#AA22FF]**for **[/COLOR]core.img. core.img is at this location and looks 
    [COLOR=#AA22FF]**for**[/COLOR] [COLOR=#666666]([/COLOR],msdos1[COLOR=#666666])[/COLOR]/boot/grub on this drive.
 [COLOR=#666666]=[/COLOR]> No boot loader is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       ext4
    Boot sector [COLOR=#AA22FF]type[/COLOR]:  -
    Boot sector info: 
    Operating System:  Ubuntu 12.04.4 LTS 
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector [COLOR=#AA22FF]type[/COLOR]:  Unknown
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       swap
    Boot sector [COLOR=#AA22FF]type[/COLOR]:  -
    Boot sector info: 

sda6: __________________________________________________________________________

    File system:       ext4
    Boot sector [COLOR=#AA22FF]type[/COLOR]:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sdb1: __________________________________________________________________________

    File system:       ext4
    Boot sector [COLOR=#AA22FF]type[/COLOR]:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

[COLOR=#666666]============================[/COLOR] Drive/Partition Info: [COLOR=#666666]=============================[/COLOR]

Drive: sda _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
[COLOR=#B8860B]Units[/COLOR] [COLOR=#666666]=[/COLOR] sectors of 1 * [COLOR=#B8860B]512[/COLOR] [COLOR=#666666]=[/COLOR] 512 bytes
Sector size [COLOR=#666666]([/COLOR]logical/physical[COLOR=#666666])[/COLOR]: 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  [COLOR=#008800]*# of Sectors  Id System*[/COLOR]

/dev/sda1    *          2,048    97,656,831    97,654,784  83 Linux
/dev/sda2          97,658,878   976,771,071   879,112,194   5 Extended
/dev/sda5          97,658,880   105,656,319     7,997,440  82 Linux swap / Solaris
/dev/sda6         105,658,368   976,771,071   871,112,704  83 Linux


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
[COLOR=#B8860B]Units[/COLOR] [COLOR=#666666]=[/COLOR] sectors of 1 * [COLOR=#B8860B]512[/COLOR] [COLOR=#666666]=[/COLOR] 512 bytes
Sector size [COLOR=#666666]([/COLOR]logical/physical[COLOR=#666666])[/COLOR]: 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  [COLOR=#008800]*# of Sectors  Id System*[/COLOR]

/dev/sdb1    *          2,048   976,771,071   976,769,024  83 Linux


[COLOR=#BB4444]"blkid"[/COLOR] output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        4e7bef02-ca63-49d7-9e41-775cf2f9803b   ext4       
/dev/sda5        2021d5eb-6df5-49b0-ab3d-2bd348e04335   swap       
/dev/sda6        39993f2b-d435-43ac-b137-5b39ac97472e   ext4       
/dev/sdb1        8722b4a4-435e-4848-bba6-45d3e8762f7d   ext4       
/dev/sr0                                                iso9660    Ubuntu precise 20120425-15:29

[COLOR=#666666]================================[/COLOR] Mount points: [COLOR=#666666]=================================[/COLOR]

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   [COLOR=#666666]([/COLOR]ro,noatime[COLOR=#666666])[/COLOR]
/dev/sr0         /cdrom                   iso9660    [COLOR=#666666]([/COLOR]ro,noatime[COLOR=#666666])[/COLOR]


[COLOR=#666666]===========================[/COLOR] sda1/boot/grub/grub.cfg: [COLOR=#666666]===========================[/COLOR]

--------------------------------------------------------------------------------
[COLOR=#008800]*#*[/COLOR]
[COLOR=#008800]*# DO NOT EDIT THIS FILE*[/COLOR]
[COLOR=#008800]*#*[/COLOR]
[COLOR=#008800]*# It is automatically generated by grub-mkconfig using templates*[/COLOR]
[COLOR=#008800]*# from /etc/grub.d and settings from /etc/default/grub*[/COLOR]
[COLOR=#008800]*#*[/COLOR]

[COLOR=#008800]*### BEGIN /etc/grub.d/00_header ###*[/COLOR]
[COLOR=#AA22FF]**if**[/COLOR] [COLOR=#666666][[/COLOR] -s [COLOR=#B8860B]$prefix[/COLOR]/grubenv [COLOR=#666666]][/COLOR]; [COLOR=#AA22FF]**then**[/COLOR]
[COLOR=#AA22FF]**  **[/COLOR][COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]have_grubenv[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#AA22FF]true[/COLOR]
[COLOR=#AA22FF]  [/COLOR]load_env
[COLOR=#AA22FF]**fi**[/COLOR]
[COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]default[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"0"[/COLOR]
[COLOR=#AA22FF]**if**[/COLOR] [COLOR=#666666][[/COLOR] [COLOR=#BB4444]"${prev_saved_entry}"[/COLOR] [COLOR=#666666]][/COLOR]; [COLOR=#AA22FF]**then**[/COLOR]
[COLOR=#AA22FF]**  **[/COLOR][COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]saved_entry[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"${prev_saved_entry}"[/COLOR]
  save_env saved_entry
  [COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]prev_saved_entry[/COLOR][COLOR=#666666]=[/COLOR]
  save_env prev_saved_entry
  [COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]boot_once[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#AA22FF]true[/COLOR]
[COLOR=#AA22FF]**fi**[/COLOR]

[COLOR=#AA22FF]**function **[/COLOR]savedefault [COLOR=#666666]{[/COLOR]
  [COLOR=#AA22FF]**if**[/COLOR] [COLOR=#666666][[/COLOR] -z [COLOR=#BB4444]"${boot_once}"[/COLOR] [COLOR=#666666]][/COLOR]; [COLOR=#AA22FF]**then**[/COLOR]
[COLOR=#AA22FF]**    **[/COLOR][COLOR=#B8860B]saved_entry[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"${chosen}"[/COLOR]
    save_env saved_entry
  [COLOR=#AA22FF]**fi**[/COLOR]
[COLOR=#666666]}[/COLOR]

[COLOR=#AA22FF]**function **[/COLOR]recordfail [COLOR=#666666]{[/COLOR]
  [COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]recordfail[/COLOR][COLOR=#666666]=[/COLOR]1
  [COLOR=#AA22FF]**if**[/COLOR] [COLOR=#666666][[/COLOR] -n [COLOR=#BB4444]"${have_grubenv}"[/COLOR] [COLOR=#666666]][/COLOR]; [COLOR=#AA22FF]**then if**[/COLOR] [COLOR=#666666][[/COLOR] -z [COLOR=#BB4444]"${boot_once}"[/COLOR] [COLOR=#666666]][/COLOR]; [COLOR=#AA22FF]**then **[/COLOR]save_env recordfail; [COLOR=#AA22FF]**fi**[/COLOR]; [COLOR=#AA22FF]**fi**[/COLOR]
[COLOR=#666666]}[/COLOR]

[COLOR=#AA22FF]**function **[/COLOR]load_video [COLOR=#666666]{[/COLOR]
  insmod vbe
  insmod vga
  insmod video_bochs
  insmod video_cirrus
[COLOR=#666666]}[/COLOR]

insmod part_msdos
insmod ext2
[COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]'(hd0,msdos1)'[/COLOR]
search --no-floppy --fs-uuid --set[COLOR=#666666]=[/COLOR]root 4e7bef02-ca63-49d7-9e41-775cf2f9803b
[COLOR=#AA22FF]**if **[/COLOR]loadfont /usr/share/grub/unicode.pf2 ; [COLOR=#AA22FF]**then**[/COLOR]
[COLOR=#AA22FF]**  **[/COLOR][COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]gfxmode[/COLOR][COLOR=#666666]=[/COLOR]auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  [COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]'(hd0,msdos1)'[/COLOR]
  search --no-floppy --fs-uuid --set[COLOR=#666666]=[/COLOR]root 4e7bef02-ca63-49d7-9e41-775cf2f9803b
  [COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]locale_dir[/COLOR][COLOR=#666666]=([/COLOR][COLOR=#B8860B]$root[/COLOR][COLOR=#666666])[/COLOR]/boot/grub/locale
  [COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]lang[/COLOR][COLOR=#666666]=[/COLOR]fr_FR
  insmod gettext
[COLOR=#AA22FF]**fi**[/COLOR]
terminal_output gfxterm
[COLOR=#AA22FF]**if**[/COLOR] [COLOR=#666666][[/COLOR] [COLOR=#BB4444]"${recordfail}"[/COLOR] [COLOR=#666666]=[/COLOR] 1 [COLOR=#666666]][/COLOR] ; [COLOR=#AA22FF]**then**[/COLOR]
[COLOR=#AA22FF]**  **[/COLOR][COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]timeout[/COLOR][COLOR=#666666]=[/COLOR]10
[COLOR=#AA22FF]**else**[/COLOR]
[COLOR=#AA22FF]**  if**[/COLOR] [COLOR=#666666][[/COLOR] x[COLOR=#B8860B]$feature_timeout_style[/COLOR] [COLOR=#666666]=[/COLOR] xy [COLOR=#666666]][/COLOR] ; [COLOR=#AA22FF]**then**[/COLOR]
[COLOR=#AA22FF]**    **[/COLOR][COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]timeout_style[/COLOR][COLOR=#666666]=[/COLOR]hidden
    [COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]timeout[/COLOR][COLOR=#666666]=[/COLOR]10
  [COLOR=#008800]*# Fallback hidden-timeout code in case the timeout_style feature is*[/COLOR]
  [COLOR=#008800]*# unavailable.*[/COLOR]
  [COLOR=#AA22FF]**elif **[/COLOR]sleep --interruptible 0 ; [COLOR=#AA22FF]**then**[/COLOR]
[COLOR=#AA22FF]**    **[/COLOR][COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]timeout[/COLOR][COLOR=#666666]=[/COLOR]10
  [COLOR=#AA22FF]**fi**[/COLOR]
[COLOR=#AA22FF]**fi**[/COLOR]
[COLOR=#008800]*### END /etc/grub.d/00_header ###*[/COLOR]

[COLOR=#008800]*### BEGIN /etc/grub.d/05_debian_theme ###*[/COLOR]
[COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]menu_color_normal[/COLOR][COLOR=#666666]=[/COLOR]white/black
[COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]menu_color_highlight[/COLOR][COLOR=#666666]=[/COLOR]black/light-gray
[COLOR=#AA22FF]**if **[/COLOR]background_color 44,0,30; [COLOR=#AA22FF]**then**[/COLOR]
[COLOR=#AA22FF]**  **[/COLOR]clear
[COLOR=#AA22FF]**fi**[/COLOR]
[COLOR=#008800]*### END /etc/grub.d/05_debian_theme ###*[/COLOR]

[COLOR=#008800]*### BEGIN /etc/grub.d/10_linux ###*[/COLOR]
[COLOR=#AA22FF]**function **[/COLOR]gfxmode [COLOR=#666666]{[/COLOR]
	[COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]gfxpayload[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"${1}"[/COLOR]
	[COLOR=#AA22FF]**if**[/COLOR] [COLOR=#666666][[/COLOR] [COLOR=#BB4444]"${1}"[/COLOR] [COLOR=#666666]=[/COLOR] [COLOR=#BB4444]"keep"[/COLOR] [COLOR=#666666]][/COLOR]; [COLOR=#AA22FF]**then**[/COLOR]
[COLOR=#AA22FF]**		**[/COLOR][COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]vt_handoff[/COLOR][COLOR=#666666]=[/COLOR]vt.handoff[COLOR=#666666]=[/COLOR]7
	[COLOR=#AA22FF]**else**[/COLOR]
[COLOR=#AA22FF]**		**[/COLOR][COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]vt_handoff[/COLOR][COLOR=#666666]=[/COLOR]
	[COLOR=#AA22FF]**fi**[/COLOR]
[COLOR=#666666]}[/COLOR]
[COLOR=#AA22FF]**if**[/COLOR] [COLOR=#666666][[/COLOR] [COLOR=#BB4444]"${recordfail}"[/COLOR] ![COLOR=#666666]=[/COLOR] 1 [COLOR=#666666]][/COLOR]; [COLOR=#AA22FF]**then**[/COLOR]
[COLOR=#AA22FF]**  if**[/COLOR] [COLOR=#666666][[/COLOR] -e [COLOR=#AA22FF]**${**[/COLOR][COLOR=#B8860B]prefix[/COLOR][COLOR=#AA22FF]**}**[/COLOR]/gfxblacklist.txt [COLOR=#666666]][/COLOR]; [COLOR=#AA22FF]**then**[/COLOR]
[COLOR=#AA22FF]**    if **[/COLOR]hwmatch [COLOR=#AA22FF]**${**[/COLOR][COLOR=#B8860B]prefix[/COLOR][COLOR=#AA22FF]**}**[/COLOR]/gfxblacklist.txt 3; [COLOR=#AA22FF]**then**[/COLOR]
[COLOR=#AA22FF]**      if**[/COLOR] [COLOR=#666666][[/COLOR] [COLOR=#AA22FF]**${**[/COLOR][COLOR=#B8860B]match[/COLOR][COLOR=#AA22FF]**}**[/COLOR] [COLOR=#666666]=[/COLOR] 0 [COLOR=#666666]][/COLOR]; [COLOR=#AA22FF]**then**[/COLOR]
[COLOR=#AA22FF]**        **[/COLOR][COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]linux_gfx_mode[/COLOR][COLOR=#666666]=[/COLOR]keep
      [COLOR=#AA22FF]**else**[/COLOR]
[COLOR=#AA22FF]**        **[/COLOR][COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]linux_gfx_mode[/COLOR][COLOR=#666666]=[/COLOR]text
      [COLOR=#AA22FF]**fi**[/COLOR]
[COLOR=#AA22FF]**    else**[/COLOR]
[COLOR=#AA22FF]**      **[/COLOR][COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]linux_gfx_mode[/COLOR][COLOR=#666666]=[/COLOR]text
    [COLOR=#AA22FF]**fi**[/COLOR]
[COLOR=#AA22FF]**  else**[/COLOR]
[COLOR=#AA22FF]**    **[/COLOR][COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]linux_gfx_mode[/COLOR][COLOR=#666666]=[/COLOR]keep
  [COLOR=#AA22FF]**fi**[/COLOR]
[COLOR=#AA22FF]**else**[/COLOR]
[COLOR=#AA22FF]**  **[/COLOR][COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]linux_gfx_mode[/COLOR][COLOR=#666666]=[/COLOR]text
[COLOR=#AA22FF]**fi**[/COLOR]
[COLOR=#AA22FF]export [/COLOR]linux_gfx_mode
[COLOR=#AA22FF]**if**[/COLOR] [COLOR=#666666][[/COLOR] [COLOR=#BB4444]"${linux_gfx_mode}"[/COLOR] ![COLOR=#666666]=[/COLOR] [COLOR=#BB4444]"text"[/COLOR] [COLOR=#666666]][/COLOR]; [COLOR=#AA22FF]**then **[/COLOR]load_video; [COLOR=#AA22FF]**fi**[/COLOR]
menuentry [COLOR=#BB4444]'Ubuntu, avec Linux 3.5.0-18-generic'[/COLOR] --class ubuntu --class gnu-linux --class gnu --class os [COLOR=#666666]{[/COLOR]
	recordfail
	gfxmode [COLOR=#B8860B]$linux_gfx_mode[/COLOR]
	insmod gzio
	insmod part_msdos
	insmod ext2
	[COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]'(hd0,msdos1)'[/COLOR]
	search --no-floppy --fs-uuid --set[COLOR=#666666]=[/COLOR]root 4e7bef02-ca63-49d7-9e41-775cf2f9803b
	linux	/boot/vmlinuz-3.5.0-18-generic [COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#B8860B]UUID[/COLOR][COLOR=#666666]=[/COLOR]4e7bef02-ca63-49d7-9e41-775cf2f9803b ro   quiet splash [COLOR=#B8860B]$vt_handoff[/COLOR]
	initrd	/boot/initrd.img-3.5.0-18-generic
[COLOR=#666666]}[/COLOR]
menuentry [COLOR=#BB4444]'Ubuntu, with Linux 3.5.0-18-generic (recovery mode)'[/COLOR] --class ubuntu --class gnu-linux --class gnu --class os [COLOR=#666666]{[/COLOR]
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	[COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]'(hd0,msdos1)'[/COLOR]
	search --no-floppy --fs-uuid --set[COLOR=#666666]=[/COLOR]root 4e7bef02-ca63-49d7-9e41-775cf2f9803b
	[COLOR=#AA22FF]echo[/COLOR]	[COLOR=#BB4444]'Chargement de Linux 3.5.0-18-generic ...'[/COLOR]
	linux	/boot/vmlinuz-3.5.0-18-generic [COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#B8860B]UUID[/COLOR][COLOR=#666666]=[/COLOR]4e7bef02-ca63-49d7-9e41-775cf2f9803b ro recovery nomodeset 
	[COLOR=#AA22FF]echo[/COLOR]	[COLOR=#BB4444]'Chargement du disque mémoire initial ...'[/COLOR]
	initrd	/boot/initrd.img-3.5.0-18-generic
[COLOR=#666666]}[/COLOR]
submenu [COLOR=#BB4444]"Previous Linux versions"[/COLOR] [COLOR=#666666]{[/COLOR]
menuentry [COLOR=#BB4444]'Ubuntu, avec Linux 3.2.0-59-generic'[/COLOR] --class ubuntu --class gnu-linux --class gnu --class os [COLOR=#666666]{[/COLOR]
	recordfail
	gfxmode [COLOR=#B8860B]$linux_gfx_mode[/COLOR]
	insmod gzio
	insmod part_msdos
	insmod ext2
	[COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]'(hd0,msdos1)'[/COLOR]
	search --no-floppy --fs-uuid --set[COLOR=#666666]=[/COLOR]root 4e7bef02-ca63-49d7-9e41-775cf2f9803b
	linux	/boot/vmlinuz-3.2.0-59-generic [COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#B8860B]UUID[/COLOR][COLOR=#666666]=[/COLOR]4e7bef02-ca63-49d7-9e41-775cf2f9803b ro   quiet splash [COLOR=#B8860B]$vt_handoff[/COLOR]
	initrd	/boot/initrd.img-3.2.0-59-generic
[COLOR=#666666]}[/COLOR]
menuentry [COLOR=#BB4444]'Ubuntu, with Linux 3.2.0-59-generic (recovery mode)'[/COLOR] --class ubuntu --class gnu-linux --class gnu --class os [COLOR=#666666]{[/COLOR]
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	[COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]'(hd0,msdos1)'[/COLOR]
	search --no-floppy --fs-uuid --set[COLOR=#666666]=[/COLOR]root 4e7bef02-ca63-49d7-9e41-775cf2f9803b
	[COLOR=#AA22FF]echo[/COLOR]	[COLOR=#BB4444]'Chargement de Linux 3.2.0-59-generic ...'[/COLOR]
	linux	/boot/vmlinuz-3.2.0-59-generic [COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#B8860B]UUID[/COLOR][COLOR=#666666]=[/COLOR]4e7bef02-ca63-49d7-9e41-775cf2f9803b ro recovery nomodeset 
	[COLOR=#AA22FF]echo[/COLOR]	[COLOR=#BB4444]'Chargement du disque mémoire initial ...'[/COLOR]
	initrd	/boot/initrd.img-3.2.0-59-generic
[COLOR=#666666]}[/COLOR]
menuentry [COLOR=#BB4444]'Ubuntu, avec Linux 3.2.0-58-generic'[/COLOR] --class ubuntu --class gnu-linux --class gnu --class os [COLOR=#666666]{[/COLOR]
	recordfail
	gfxmode [COLOR=#B8860B]$linux_gfx_mode[/COLOR]
	insmod gzio
	insmod part_msdos
	insmod ext2
	[COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]'(hd0,msdos1)'[/COLOR]
	search --no-floppy --fs-uuid --set[COLOR=#666666]=[/COLOR]root 4e7bef02-ca63-49d7-9e41-775cf2f9803b
	linux	/boot/vmlinuz-3.2.0-58-generic [COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#B8860B]UUID[/COLOR][COLOR=#666666]=[/COLOR]4e7bef02-ca63-49d7-9e41-775cf2f9803b ro   quiet splash [COLOR=#B8860B]$vt_handoff[/COLOR]
	initrd	/boot/initrd.img-3.2.0-58-generic
[COLOR=#666666]}[/COLOR]
menuentry [COLOR=#BB4444]'Ubuntu, with Linux 3.2.0-58-generic (recovery mode)'[/COLOR] --class ubuntu --class gnu-linux --class gnu --class os [COLOR=#666666]{[/COLOR]
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	[COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]'(hd0,msdos1)'[/COLOR]
	search --no-floppy --fs-uuid --set[COLOR=#666666]=[/COLOR]root 4e7bef02-ca63-49d7-9e41-775cf2f9803b
	[COLOR=#AA22FF]echo[/COLOR]	[COLOR=#BB4444]'Chargement de Linux 3.2.0-58-generic ...'[/COLOR]
	linux	/boot/vmlinuz-3.2.0-58-generic [COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#B8860B]UUID[/COLOR][COLOR=#666666]=[/COLOR]4e7bef02-ca63-49d7-9e41-775cf2f9803b ro recovery nomodeset 
	[COLOR=#AA22FF]echo[/COLOR]	[COLOR=#BB4444]'Chargement du disque mémoire initial ...'[/COLOR]
	initrd	/boot/initrd.img-3.2.0-58-generic
[COLOR=#666666]}[/COLOR]
menuentry [COLOR=#BB4444]'Ubuntu, avec Linux 3.2.0-57-generic'[/COLOR] --class ubuntu --class gnu-linux --class gnu --class os [COLOR=#666666]{[/COLOR]
	recordfail
	gfxmode [COLOR=#B8860B]$linux_gfx_mode[/COLOR]
	insmod gzio
	insmod part_msdos
	insmod ext2
	[COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]'(hd0,msdos1)'[/COLOR]
	search --no-floppy --fs-uuid --set[COLOR=#666666]=[/COLOR]root 4e7bef02-ca63-49d7-9e41-775cf2f9803b
	linux	/boot/vmlinuz-3.2.0-57-generic [COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#B8860B]UUID[/COLOR][COLOR=#666666]=[/COLOR]4e7bef02-ca63-49d7-9e41-775cf2f9803b ro   quiet splash [COLOR=#B8860B]$vt_handoff[/COLOR]
	initrd	/boot/initrd.img-3.2.0-57-generic
[COLOR=#666666]}[/COLOR]
menuentry [COLOR=#BB4444]'Ubuntu, with Linux 3.2.0-57-generic (recovery mode)'[/COLOR] --class ubuntu --class gnu-linux --class gnu --class os [COLOR=#666666]{[/COLOR]
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	[COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]'(hd0,msdos1)'[/COLOR]
	search --no-floppy --fs-uuid --set[COLOR=#666666]=[/COLOR]root 4e7bef02-ca63-49d7-9e41-775cf2f9803b
	[COLOR=#AA22FF]echo[/COLOR]	[COLOR=#BB4444]'Chargement de Linux 3.2.0-57-generic ...'[/COLOR]
	linux	/boot/vmlinuz-3.2.0-57-generic [COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#B8860B]UUID[/COLOR][COLOR=#666666]=[/COLOR]4e7bef02-ca63-49d7-9e41-775cf2f9803b ro recovery nomodeset 
	[COLOR=#AA22FF]echo[/COLOR]	[COLOR=#BB4444]'Chargement du disque mémoire initial ...'[/COLOR]
	initrd	/boot/initrd.img-3.2.0-57-generic
[COLOR=#666666]}[/COLOR]
menuentry [COLOR=#BB4444]'Ubuntu, avec Linux 3.2.0-56-generic'[/COLOR] --class ubuntu --class gnu-linux --class gnu --class os [COLOR=#666666]{[/COLOR]
	recordfail
	gfxmode [COLOR=#B8860B]$linux_gfx_mode[/COLOR]
	insmod gzio
	insmod part_msdos
	insmod ext2
	[COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]'(hd0,msdos1)'[/COLOR]
	search --no-floppy --fs-uuid --set[COLOR=#666666]=[/COLOR]root 4e7bef02-ca63-49d7-9e41-775cf2f9803b
	linux	/boot/vmlinuz-3.2.0-56-generic [COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#B8860B]UUID[/COLOR][COLOR=#666666]=[/COLOR]4e7bef02-ca63-49d7-9e41-775cf2f9803b ro   quiet splash [COLOR=#B8860B]$vt_handoff[/COLOR]
	initrd	/boot/initrd.img-3.2.0-56-generic
[COLOR=#666666]}[/COLOR]
menuentry [COLOR=#BB4444]'Ubuntu, with Linux 3.2.0-56-generic (recovery mode)'[/COLOR] --class ubuntu --class gnu-linux --class gnu --class os [COLOR=#666666]{[/COLOR]
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	[COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]'(hd0,msdos1)'[/COLOR]
	search --no-floppy --fs-uuid --set[COLOR=#666666]=[/COLOR]root 4e7bef02-ca63-49d7-9e41-775cf2f9803b
	[COLOR=#AA22FF]echo[/COLOR]	[COLOR=#BB4444]'Chargement de Linux 3.2.0-56-generic ...'[/COLOR]
	linux	/boot/vmlinuz-3.2.0-56-generic [COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#B8860B]UUID[/COLOR][COLOR=#666666]=[/COLOR]4e7bef02-ca63-49d7-9e41-775cf2f9803b ro recovery nomodeset 
	[COLOR=#AA22FF]echo[/COLOR]	[COLOR=#BB4444]'Chargement du disque mémoire initial ...'[/COLOR]
	initrd	/boot/initrd.img-3.2.0-56-generic
[COLOR=#666666]}[/COLOR]
menuentry [COLOR=#BB4444]'Ubuntu, avec Linux 3.2.0-55-generic'[/COLOR] --class ubuntu --class gnu-linux --class gnu --class os [COLOR=#666666]{[/COLOR]
	recordfail
	gfxmode [COLOR=#B8860B]$linux_gfx_mode[/COLOR]
	insmod gzio
	insmod part_msdos
	insmod ext2
	[COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]'(hd0,msdos1)'[/COLOR]
	search --no-floppy --fs-uuid --set[COLOR=#666666]=[/COLOR]root 4e7bef02-ca63-49d7-9e41-775cf2f9803b
	linux	/boot/vmlinuz-3.2.0-55-generic [COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#B8860B]UUID[/COLOR][COLOR=#666666]=[/COLOR]4e7bef02-ca63-49d7-9e41-775cf2f9803b ro   quiet splash [COLOR=#B8860B]$vt_handoff[/COLOR]
	initrd	/boot/initrd.img-3.2.0-55-generic
[COLOR=#666666]}[/COLOR]
menuentry [COLOR=#BB4444]'Ubuntu, with Linux 3.2.0-55-generic (recovery mode)'[/COLOR] --class ubuntu --class gnu-linux --class gnu --class os [COLOR=#666666]{[/COLOR]
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	[COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]'(hd0,msdos1)'[/COLOR]
	search --no-floppy --fs-uuid --set[COLOR=#666666]=[/COLOR]root 4e7bef02-ca63-49d7-9e41-775cf2f9803b
	[COLOR=#AA22FF]echo[/COLOR]	[COLOR=#BB4444]'Chargement de Linux 3.2.0-55-generic ...'[/COLOR]
	linux	/boot/vmlinuz-3.2.0-55-generic [COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#B8860B]UUID[/COLOR][COLOR=#666666]=[/COLOR]4e7bef02-ca63-49d7-9e41-775cf2f9803b ro recovery nomodeset 
	[COLOR=#AA22FF]echo[/COLOR]	[COLOR=#BB4444]'Chargement du disque mémoire initial ...'[/COLOR]
	initrd	/boot/initrd.img-3.2.0-55-generic
[COLOR=#666666]}[/COLOR]
menuentry [COLOR=#BB4444]'Ubuntu, avec Linux 3.2.0-54-generic'[/COLOR] --class ubuntu --class gnu-linux --class gnu --class os [COLOR=#666666]{[/COLOR]
	recordfail
	gfxmode [COLOR=#B8860B]$linux_gfx_mode[/COLOR]
	insmod gzio
	insmod part_msdos
	insmod ext2
	[COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]'(hd0,msdos1)'[/COLOR]
	search --no-floppy --fs-uuid --set[COLOR=#666666]=[/COLOR]root 4e7bef02-ca63-49d7-9e41-775cf2f9803b
	linux	/boot/vmlinuz-3.2.0-54-generic [COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#B8860B]UUID[/COLOR][COLOR=#666666]=[/COLOR]4e7bef02-ca63-49d7-9e41-775cf2f9803b ro   quiet splash [COLOR=#B8860B]$vt_handoff[/COLOR]
	initrd	/boot/initrd.img-3.2.0-54-generic
[COLOR=#666666]}[/COLOR]
menuentry [COLOR=#BB4444]'Ubuntu, with Linux 3.2.0-54-generic (recovery mode)'[/COLOR] --class ubuntu --class gnu-linux --class gnu --class os [COLOR=#666666]{[/COLOR]
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	[COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]'(hd0,msdos1)'[/COLOR]
	search --no-floppy --fs-uuid --set[COLOR=#666666]=[/COLOR]root 4e7bef02-ca63-49d7-9e41-775cf2f9803b
	[COLOR=#AA22FF]echo[/COLOR]	[COLOR=#BB4444]'Chargement de Linux 3.2.0-54-generic ...'[/COLOR]
	linux	/boot/vmlinuz-3.2.0-54-generic [COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#B8860B]UUID[/COLOR][COLOR=#666666]=[/COLOR]4e7bef02-ca63-49d7-9e41-775cf2f9803b ro recovery nomodeset 
	[COLOR=#AA22FF]echo[/COLOR]	[COLOR=#BB4444]'Chargement du disque mémoire initial ...'[/COLOR]
	initrd	/boot/initrd.img-3.2.0-54-generic
[COLOR=#666666]}[/COLOR]
menuentry [COLOR=#BB4444]'Ubuntu, avec Linux 3.2.0-53-generic'[/COLOR] --class ubuntu --class gnu-linux --class gnu --class os [COLOR=#666666]{[/COLOR]
	recordfail
	gfxmode [COLOR=#B8860B]$linux_gfx_mode[/COLOR]
	insmod gzio
	insmod part_msdos
	insmod ext2
	[COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]'(hd0,msdos1)'[/COLOR]
	search --no-floppy --fs-uuid --set[COLOR=#666666]=[/COLOR]root 4e7bef02-ca63-49d7-9e41-775cf2f9803b
	linux	/boot/vmlinuz-3.2.0-53-generic [COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#B8860B]UUID[/COLOR][COLOR=#666666]=[/COLOR]4e7bef02-ca63-49d7-9e41-775cf2f9803b ro   quiet splash [COLOR=#B8860B]$vt_handoff[/COLOR]
	initrd	/boot/initrd.img-3.2.0-53-generic
[COLOR=#666666]}[/COLOR]
menuentry [COLOR=#BB4444]'Ubuntu, with Linux 3.2.0-53-generic (recovery mode)'[/COLOR] --class ubuntu --class gnu-linux --class gnu --class os [COLOR=#666666]{[/COLOR]
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	[COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]'(hd0,msdos1)'[/COLOR]
	search --no-floppy --fs-uuid --set[COLOR=#666666]=[/COLOR]root 4e7bef02-ca63-49d7-9e41-775cf2f9803b
	[COLOR=#AA22FF]echo[/COLOR]	[COLOR=#BB4444]'Chargement de Linux 3.2.0-53-generic ...'[/COLOR]
	linux	/boot/vmlinuz-3.2.0-53-generic [COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#B8860B]UUID[/COLOR][COLOR=#666666]=[/COLOR]4e7bef02-ca63-49d7-9e41-775cf2f9803b ro recovery nomodeset 
	[COLOR=#AA22FF]echo[/COLOR]	[COLOR=#BB4444]'Chargement du disque mémoire initial ...'[/COLOR]
	initrd	/boot/initrd.img-3.2.0-53-generic
[COLOR=#666666]}[/COLOR]
menuentry [COLOR=#BB4444]'Ubuntu, avec Linux 3.2.0-52-generic'[/COLOR] --class ubuntu --class gnu-linux --class gnu --class os [COLOR=#666666]{[/COLOR]
	recordfail
	gfxmode [COLOR=#B8860B]$linux_gfx_mode[/COLOR]
	insmod gzio
	insmod part_msdos
	insmod ext2
	[COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]'(hd0,msdos1)'[/COLOR]
	search --no-floppy --fs-uuid --set[COLOR=#666666]=[/COLOR]root 4e7bef02-ca63-49d7-9e41-775cf2f9803b
	linux	/boot/vmlinuz-3.2.0-52-generic [COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#B8860B]UUID[/COLOR][COLOR=#666666]=[/COLOR]4e7bef02-ca63-49d7-9e41-775cf2f9803b ro   quiet splash [COLOR=#B8860B]$vt_handoff[/COLOR]
	initrd	/boot/initrd.img-3.2.0-52-generic
[COLOR=#666666]}[/COLOR]
menuentry [COLOR=#BB4444]'Ubuntu, with Linux 3.2.0-52-generic (recovery mode)'[/COLOR] --class ubuntu --class gnu-linux --class gnu --class os [COLOR=#666666]{[/COLOR]
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	[COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]'(hd0,msdos1)'[/COLOR]
	search --no-floppy --fs-uuid --set[COLOR=#666666]=[/COLOR]root 4e7bef02-ca63-49d7-9e41-775cf2f9803b
	[COLOR=#AA22FF]echo[/COLOR]	[COLOR=#BB4444]'Chargement de Linux 3.2.0-52-generic ...'[/COLOR]
	linux	/boot/vmlinuz-3.2.0-52-generic [COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#B8860B]UUID[/COLOR][COLOR=#666666]=[/COLOR]4e7bef02-ca63-49d7-9e41-775cf2f9803b ro recovery nomodeset 
	[COLOR=#AA22FF]echo[/COLOR]	[COLOR=#BB4444]'Chargement du disque mémoire initial ...'[/COLOR]
	initrd	/boot/initrd.img-3.2.0-52-generic
[COLOR=#666666]}[/COLOR]
menuentry [COLOR=#BB4444]'Ubuntu, avec Linux 3.2.0-51-generic'[/COLOR] --class ubuntu --class gnu-linux --class gnu --class os [COLOR=#666666]{[/COLOR]
	recordfail
	gfxmode [COLOR=#B8860B]$linux_gfx_mode[/COLOR]
	insmod gzio
	insmod part_msdos
	insmod ext2
	[COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]'(hd0,msdos1)'[/COLOR]
	search --no-floppy --fs-uuid --set[COLOR=#666666]=[/COLOR]root 4e7bef02-ca63-49d7-9e41-775cf2f9803b
	linux	/boot/vmlinuz-3.2.0-51-generic [COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#B8860B]UUID[/COLOR][COLOR=#666666]=[/COLOR]4e7bef02-ca63-49d7-9e41-775cf2f9803b ro   quiet splash [COLOR=#B8860B]$vt_handoff[/COLOR]
	initrd	/boot/initrd.img-3.2.0-51-generic
[COLOR=#666666]}[/COLOR]
menuentry [COLOR=#BB4444]'Ubuntu, with Linux 3.2.0-51-generic (recovery mode)'[/COLOR] --class ubuntu --class gnu-linux --class gnu --class os [COLOR=#666666]{[/COLOR]
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	[COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]'(hd0,msdos1)'[/COLOR]
	search --no-floppy --fs-uuid --set[COLOR=#666666]=[/COLOR]root 4e7bef02-ca63-49d7-9e41-775cf2f9803b
	[COLOR=#AA22FF]echo[/COLOR]	[COLOR=#BB4444]'Chargement de Linux 3.2.0-51-generic ...'[/COLOR]
	linux	/boot/vmlinuz-3.2.0-51-generic [COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#B8860B]UUID[/COLOR][COLOR=#666666]=[/COLOR]4e7bef02-ca63-49d7-9e41-775cf2f9803b ro recovery nomodeset 
	[COLOR=#AA22FF]echo[/COLOR]	[COLOR=#BB4444]'Chargement du disque mémoire initial ...'[/COLOR]
	initrd	/boot/initrd.img-3.2.0-51-generic
[COLOR=#666666]}[/COLOR]
menuentry [COLOR=#BB4444]'Ubuntu, avec Linux 3.2.0-49-generic'[/COLOR] --class ubuntu --class gnu-linux --class gnu --class os [COLOR=#666666]{[/COLOR]
	recordfail
	gfxmode [COLOR=#B8860B]$linux_gfx_mode[/COLOR]
	insmod gzio
	insmod part_msdos
	insmod ext2
	[COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]'(hd0,msdos1)'[/COLOR]
	search --no-floppy --fs-uuid --set[COLOR=#666666]=[/COLOR]root 4e7bef02-ca63-49d7-9e41-775cf2f9803b
	linux	/boot/vmlinuz-3.2.0-49-generic [COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#B8860B]UUID[/COLOR][COLOR=#666666]=[/COLOR]4e7bef02-ca63-49d7-9e41-775cf2f9803b ro   quiet splash [COLOR=#B8860B]$vt_handoff[/COLOR]
	initrd	/boot/initrd.img-3.2.0-49-generic
[COLOR=#666666]}[/COLOR]
menuentry [COLOR=#BB4444]'Ubuntu, with Linux 3.2.0-49-generic (recovery mode)'[/COLOR] --class ubuntu --class gnu-linux --class gnu --class os [COLOR=#666666]{[/COLOR]
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	[COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]'(hd0,msdos1)'[/COLOR]
	search --no-floppy --fs-uuid --set[COLOR=#666666]=[/COLOR]root 4e7bef02-ca63-49d7-9e41-775cf2f9803b
	[COLOR=#AA22FF]echo[/COLOR]	[COLOR=#BB4444]'Chargement de Linux 3.2.0-49-generic ...'[/COLOR]
	linux	/boot/vmlinuz-3.2.0-49-generic [COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#B8860B]UUID[/COLOR][COLOR=#666666]=[/COLOR]4e7bef02-ca63-49d7-9e41-775cf2f9803b ro recovery nomodeset 
	[COLOR=#AA22FF]echo[/COLOR]	[COLOR=#BB4444]'Chargement du disque mémoire initial ...'[/COLOR]
	initrd	/boot/initrd.img-3.2.0-49-generic
[COLOR=#666666]}[/COLOR]
menuentry [COLOR=#BB4444]'Ubuntu, avec Linux 3.2.0-48-generic'[/COLOR] --class ubuntu --class gnu-linux --class gnu --class os [COLOR=#666666]{[/COLOR]
	recordfail
	gfxmode [COLOR=#B8860B]$linux_gfx_mode[/COLOR]
	insmod gzio
	insmod part_msdos
	insmod ext2
	[COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]'(hd0,msdos1)'[/COLOR]
	search --no-floppy --fs-uuid --set[COLOR=#666666]=[/COLOR]root 4e7bef02-ca63-49d7-9e41-775cf2f9803b
	linux	/boot/vmlinuz-3.2.0-48-generic [COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#B8860B]UUID[/COLOR][COLOR=#666666]=[/COLOR]4e7bef02-ca63-49d7-9e41-775cf2f9803b ro   quiet splash [COLOR=#B8860B]$vt_handoff[/COLOR]
	initrd	/boot/initrd.img-3.2.0-48-generic
[COLOR=#666666]}[/COLOR]
menuentry [COLOR=#BB4444]'Ubuntu, with Linux 3.2.0-48-generic (recovery mode)'[/COLOR] --class ubuntu --class gnu-linux --class gnu --class os [COLOR=#666666]{[/COLOR]
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	[COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]'(hd0,msdos1)'[/COLOR]
	search --no-floppy --fs-uuid --set[COLOR=#666666]=[/COLOR]root 4e7bef02-ca63-49d7-9e41-775cf2f9803b
	[COLOR=#AA22FF]echo[/COLOR]	[COLOR=#BB4444]'Chargement de Linux 3.2.0-48-generic ...'[/COLOR]
	linux	/boot/vmlinuz-3.2.0-48-generic [COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#B8860B]UUID[/COLOR][COLOR=#666666]=[/COLOR]4e7bef02-ca63-49d7-9e41-775cf2f9803b ro recovery nomodeset 
	[COLOR=#AA22FF]echo[/COLOR]	[COLOR=#BB4444]'Chargement du disque mémoire initial ...'[/COLOR]
	initrd	/boot/initrd.img-3.2.0-48-generic
[COLOR=#666666]}[/COLOR]
menuentry [COLOR=#BB4444]'Ubuntu, avec Linux 3.2.0-45-generic'[/COLOR] --class ubuntu --class gnu-linux --class gnu --class os [COLOR=#666666]{[/COLOR]
	recordfail
	gfxmode [COLOR=#B8860B]$linux_gfx_mode[/COLOR]
	insmod gzio
	insmod part_msdos
	insmod ext2
	[COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]'(hd0,msdos1)'[/COLOR]
	search --no-floppy --fs-uuid --set[COLOR=#666666]=[/COLOR]root 4e7bef02-ca63-49d7-9e41-775cf2f9803b
	linux	/boot/vmlinuz-3.2.0-45-generic [COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#B8860B]UUID[/COLOR][COLOR=#666666]=[/COLOR]4e7bef02-ca63-49d7-9e41-775cf2f9803b ro   quiet splash [COLOR=#B8860B]$vt_handoff[/COLOR]
	initrd	/boot/initrd.img-3.2.0-45-generic
[COLOR=#666666]}[/COLOR]
menuentry [COLOR=#BB4444]'Ubuntu, with Linux 3.2.0-45-generic (recovery mode)'[/COLOR] --class ubuntu --class gnu-linux --class gnu --class os [COLOR=#666666]{[/COLOR]
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	[COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]'(hd0,msdos1)'[/COLOR]
	search --no-floppy --fs-uuid --set[COLOR=#666666]=[/COLOR]root 4e7bef02-ca63-49d7-9e41-775cf2f9803b
	[COLOR=#AA22FF]echo[/COLOR]	[COLOR=#BB4444]'Chargement de Linux 3.2.0-45-generic ...'[/COLOR]
	linux	/boot/vmlinuz-3.2.0-45-generic [COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#B8860B]UUID[/COLOR][COLOR=#666666]=[/COLOR]4e7bef02-ca63-49d7-9e41-775cf2f9803b ro recovery nomodeset 
	[COLOR=#AA22FF]echo[/COLOR]	[COLOR=#BB4444]'Chargement du disque mémoire initial ...'[/COLOR]
	initrd	/boot/initrd.img-3.2.0-45-generic
[COLOR=#666666]}[/COLOR]
menuentry [COLOR=#BB4444]'Ubuntu, avec Linux 3.2.0-44-generic'[/COLOR] --class ubuntu --class gnu-linux --class gnu --class os [COLOR=#666666]{[/COLOR]
	recordfail
	gfxmode [COLOR=#B8860B]$linux_gfx_mode[/COLOR]
	insmod gzio
	insmod part_msdos
	insmod ext2
	[COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]'(hd0,msdos1)'[/COLOR]
	search --no-floppy --fs-uuid --set[COLOR=#666666]=[/COLOR]root 4e7bef02-ca63-49d7-9e41-775cf2f9803b
	linux	/boot/vmlinuz-3.2.0-44-generic [COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#B8860B]UUID[/COLOR][COLOR=#666666]=[/COLOR]4e7bef02-ca63-49d7-9e41-775cf2f9803b ro   quiet splash [COLOR=#B8860B]$vt_handoff[/COLOR]
	initrd	/boot/initrd.img-3.2.0-44-generic
[COLOR=#666666]}[/COLOR]
menuentry [COLOR=#BB4444]'Ubuntu, with Linux 3.2.0-44-generic (recovery mode)'[/COLOR] --class ubuntu --class gnu-linux --class gnu --class os [COLOR=#666666]{[/COLOR]
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	[COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]'(hd0,msdos1)'[/COLOR]
	search --no-floppy --fs-uuid --set[COLOR=#666666]=[/COLOR]root 4e7bef02-ca63-49d7-9e41-775cf2f9803b
	[COLOR=#AA22FF]echo[/COLOR]	[COLOR=#BB4444]'Chargement de Linux 3.2.0-44-generic ...'[/COLOR]
	linux	/boot/vmlinuz-3.2.0-44-generic [COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#B8860B]UUID[/COLOR][COLOR=#666666]=[/COLOR]4e7bef02-ca63-49d7-9e41-775cf2f9803b ro recovery nomodeset 
	[COLOR=#AA22FF]echo[/COLOR]	[COLOR=#BB4444]'Chargement du disque mémoire initial ...'[/COLOR]
	initrd	/boot/initrd.img-3.2.0-44-generic
[COLOR=#666666]}[/COLOR]
menuentry [COLOR=#BB4444]'Ubuntu, avec Linux 3.2.0-43-generic'[/COLOR] --class ubuntu --class gnu-linux --class gnu --class os [COLOR=#666666]{[/COLOR]
	recordfail
	gfxmode [COLOR=#B8860B]$linux_gfx_mode[/COLOR]
	insmod gzio
	insmod part_msdos
	insmod ext2
	[COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]'(hd0,msdos1)'[/COLOR]
	search --no-floppy --fs-uuid --set[COLOR=#666666]=[/COLOR]root 4e7bef02-ca63-49d7-9e41-775cf2f9803b
	linux	/boot/vmlinuz-3.2.0-43-generic [COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#B8860B]UUID[/COLOR][COLOR=#666666]=[/COLOR]4e7bef02-ca63-49d7-9e41-775cf2f9803b ro   quiet splash [COLOR=#B8860B]$vt_handoff[/COLOR]
	initrd	/boot/initrd.img-3.2.0-43-generic
[COLOR=#666666]}[/COLOR]
menuentry [COLOR=#BB4444]'Ubuntu, with Linux 3.2.0-43-generic (recovery mode)'[/COLOR] --class ubuntu --class gnu-linux --class gnu --class os [COLOR=#666666]{[/COLOR]
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	[COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]'(hd0,msdos1)'[/COLOR]
	search --no-floppy --fs-uuid --set[COLOR=#666666]=[/COLOR]root 4e7bef02-ca63-49d7-9e41-775cf2f9803b
	[COLOR=#AA22FF]echo[/COLOR]	[COLOR=#BB4444]'Chargement de Linux 3.2.0-43-generic ...'[/COLOR]
	linux	/boot/vmlinuz-3.2.0-43-generic [COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#B8860B]UUID[/COLOR][COLOR=#666666]=[/COLOR]4e7bef02-ca63-49d7-9e41-775cf2f9803b ro recovery nomodeset 
	[COLOR=#AA22FF]echo[/COLOR]	[COLOR=#BB4444]'Chargement du disque mémoire initial ...'[/COLOR]
	initrd	/boot/initrd.img-3.2.0-43-generic
[COLOR=#666666]}[/COLOR]
menuentry [COLOR=#BB4444]'Ubuntu, avec Linux 2.6.32-47-generic'[/COLOR] --class ubuntu --class gnu-linux --class gnu --class os [COLOR=#666666]{[/COLOR]
	recordfail
	gfxmode [COLOR=#B8860B]$linux_gfx_mode[/COLOR]
	insmod gzio
	insmod part_msdos
	insmod ext2
	[COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]'(hd0,msdos1)'[/COLOR]
	search --no-floppy --fs-uuid --set[COLOR=#666666]=[/COLOR]root 4e7bef02-ca63-49d7-9e41-775cf2f9803b
	linux	/boot/vmlinuz-2.6.32-47-generic [COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#B8860B]UUID[/COLOR][COLOR=#666666]=[/COLOR]4e7bef02-ca63-49d7-9e41-775cf2f9803b ro   quiet splash [COLOR=#B8860B]$vt_handoff[/COLOR]
	initrd	/boot/initrd.img-2.6.32-47-generic
[COLOR=#666666]}[/COLOR]
menuentry [COLOR=#BB4444]'Ubuntu, with Linux 2.6.32-47-generic (recovery mode)'[/COLOR] --class ubuntu --class gnu-linux --class gnu --class os [COLOR=#666666]{[/COLOR]
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	[COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]'(hd0,msdos1)'[/COLOR]
	search --no-floppy --fs-uuid --set[COLOR=#666666]=[/COLOR]root 4e7bef02-ca63-49d7-9e41-775cf2f9803b
	[COLOR=#AA22FF]echo[/COLOR]	[COLOR=#BB4444]'Chargement de Linux 2.6.32-47-generic ...'[/COLOR]
	linux	/boot/vmlinuz-2.6.32-47-generic [COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#B8860B]UUID[/COLOR][COLOR=#666666]=[/COLOR]4e7bef02-ca63-49d7-9e41-775cf2f9803b ro recovery nomodeset 
	[COLOR=#AA22FF]echo[/COLOR]	[COLOR=#BB4444]'Chargement du disque mémoire initial ...'[/COLOR]
	initrd	/boot/initrd.img-2.6.32-47-generic
[COLOR=#666666]}[/COLOR]
menuentry [COLOR=#BB4444]'Ubuntu, avec Linux 2.6.32-46-generic'[/COLOR] --class ubuntu --class gnu-linux --class gnu --class os [COLOR=#666666]{[/COLOR]
	recordfail
	gfxmode [COLOR=#B8860B]$linux_gfx_mode[/COLOR]
	insmod gzio
	insmod part_msdos
	insmod ext2
	[COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]'(hd0,msdos1)'[/COLOR]
	search --no-floppy --fs-uuid --set[COLOR=#666666]=[/COLOR]root 4e7bef02-ca63-49d7-9e41-775cf2f9803b
	linux	/boot/vmlinuz-2.6.32-46-generic [COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#B8860B]UUID[/COLOR][COLOR=#666666]=[/COLOR]4e7bef02-ca63-49d7-9e41-775cf2f9803b ro   quiet splash [COLOR=#B8860B]$vt_handoff[/COLOR]
	initrd	/boot/initrd.img-2.6.32-46-generic
[COLOR=#666666]}[/COLOR]
menuentry [COLOR=#BB4444]'Ubuntu, with Linux 2.6.32-46-generic (recovery mode)'[/COLOR] --class ubuntu --class gnu-linux --class gnu --class os [COLOR=#666666]{[/COLOR]
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	[COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]'(hd0,msdos1)'[/COLOR]
	search --no-floppy --fs-uuid --set[COLOR=#666666]=[/COLOR]root 4e7bef02-ca63-49d7-9e41-775cf2f9803b
	[COLOR=#AA22FF]echo[/COLOR]	[COLOR=#BB4444]'Chargement de Linux 2.6.32-46-generic ...'[/COLOR]
	linux	/boot/vmlinuz-2.6.32-46-generic [COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#B8860B]UUID[/COLOR][COLOR=#666666]=[/COLOR]4e7bef02-ca63-49d7-9e41-775cf2f9803b ro recovery nomodeset 
	[COLOR=#AA22FF]echo[/COLOR]	[COLOR=#BB4444]'Chargement du disque mémoire initial ...'[/COLOR]
	initrd	/boot/initrd.img-2.6.32-46-generic
[COLOR=#666666]}[/COLOR]
menuentry [COLOR=#BB4444]'Ubuntu, avec Linux 2.6.32-45-generic'[/COLOR] --class ubuntu --class gnu-linux --class gnu --class os [COLOR=#666666]{[/COLOR]
	recordfail
	gfxmode [COLOR=#B8860B]$linux_gfx_mode[/COLOR]
	insmod gzio
	insmod part_msdos
	insmod ext2
	[COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]'(hd0,msdos1)'[/COLOR]
	search --no-floppy --fs-uuid --set[COLOR=#666666]=[/COLOR]root 4e7bef02-ca63-49d7-9e41-775cf2f9803b
	linux	/boot/vmlinuz-2.6.32-45-generic [COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#B8860B]UUID[/COLOR][COLOR=#666666]=[/COLOR]4e7bef02-ca63-49d7-9e41-775cf2f9803b ro   quiet splash [COLOR=#B8860B]$vt_handoff[/COLOR]
	initrd	/boot/initrd.img-2.6.32-45-generic
[COLOR=#666666]}[/COLOR]
menuentry [COLOR=#BB4444]'Ubuntu, with Linux 2.6.32-45-generic (recovery mode)'[/COLOR] --class ubuntu --class gnu-linux --class gnu --class os [COLOR=#666666]{[/COLOR]
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	[COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]'(hd0,msdos1)'[/COLOR]
	search --no-floppy --fs-uuid --set[COLOR=#666666]=[/COLOR]root 4e7bef02-ca63-49d7-9e41-775cf2f9803b
	[COLOR=#AA22FF]echo[/COLOR]	[COLOR=#BB4444]'Chargement de Linux 2.6.32-45-generic ...'[/COLOR]
	linux	/boot/vmlinuz-2.6.32-45-generic [COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#B8860B]UUID[/COLOR][COLOR=#666666]=[/COLOR]4e7bef02-ca63-49d7-9e41-775cf2f9803b ro recovery nomodeset 
	[COLOR=#AA22FF]echo[/COLOR]	[COLOR=#BB4444]'Chargement du disque mémoire initial ...'[/COLOR]
	initrd	/boot/initrd.img-2.6.32-45-generic
[COLOR=#666666]}[/COLOR]
menuentry [COLOR=#BB4444]'Ubuntu, avec Linux 2.6.32-44-generic'[/COLOR] --class ubuntu --class gnu-linux --class gnu --class os [COLOR=#666666]{[/COLOR]
	recordfail
	gfxmode [COLOR=#B8860B]$linux_gfx_mode[/COLOR]
	insmod gzio
	insmod part_msdos
	insmod ext2
	[COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]'(hd0,msdos1)'[/COLOR]
	search --no-floppy --fs-uuid --set[COLOR=#666666]=[/COLOR]root 4e7bef02-ca63-49d7-9e41-775cf2f9803b
	linux	/boot/vmlinuz-2.6.32-44-generic [COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#B8860B]UUID[/COLOR][COLOR=#666666]=[/COLOR]4e7bef02-ca63-49d7-9e41-775cf2f9803b ro   quiet splash [COLOR=#B8860B]$vt_handoff[/COLOR]
	initrd	/boot/initrd.img-2.6.32-44-generic
[COLOR=#666666]}[/COLOR]
menuentry [COLOR=#BB4444]'Ubuntu, with Linux 2.6.32-44-generic (recovery mode)'[/COLOR] --class ubuntu --class gnu-linux --class gnu --class os [COLOR=#666666]{[/COLOR]
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	[COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]'(hd0,msdos1)'[/COLOR]
	search --no-floppy --fs-uuid --set[COLOR=#666666]=[/COLOR]root 4e7bef02-ca63-49d7-9e41-775cf2f9803b
	[COLOR=#AA22FF]echo[/COLOR]	[COLOR=#BB4444]'Chargement de Linux 2.6.32-44-generic ...'[/COLOR]
	linux	/boot/vmlinuz-2.6.32-44-generic [COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#B8860B]UUID[/COLOR][COLOR=#666666]=[/COLOR]4e7bef02-ca63-49d7-9e41-775cf2f9803b ro recovery nomodeset 
	[COLOR=#AA22FF]echo[/COLOR]	[COLOR=#BB4444]'Chargement du disque mémoire initial ...'[/COLOR]
	initrd	/boot/initrd.img-2.6.32-44-generic
[COLOR=#666666]}[/COLOR]
menuentry [COLOR=#BB4444]'Ubuntu, avec Linux 2.6.32-43-generic'[/COLOR] --class ubuntu --class gnu-linux --class gnu --class os [COLOR=#666666]{[/COLOR]
	recordfail
	gfxmode [COLOR=#B8860B]$linux_gfx_mode[/COLOR]
	insmod gzio
	insmod part_msdos
	insmod ext2
	[COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]'(hd0,msdos1)'[/COLOR]
	search --no-floppy --fs-uuid --set[COLOR=#666666]=[/COLOR]root 4e7bef02-ca63-49d7-9e41-775cf2f9803b
	linux	/boot/vmlinuz-2.6.32-43-generic [COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#B8860B]UUID[/COLOR][COLOR=#666666]=[/COLOR]4e7bef02-ca63-49d7-9e41-775cf2f9803b ro   quiet splash [COLOR=#B8860B]$vt_handoff[/COLOR]
	initrd	/boot/initrd.img-2.6.32-43-generic
[COLOR=#666666]}[/COLOR]
menuentry [COLOR=#BB4444]'Ubuntu, with Linux 2.6.32-43-generic (recovery mode)'[/COLOR] --class ubuntu --class gnu-linux --class gnu --class os [COLOR=#666666]{[/COLOR]
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	[COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]'(hd0,msdos1)'[/COLOR]
	search --no-floppy --fs-uuid --set[COLOR=#666666]=[/COLOR]root 4e7bef02-ca63-49d7-9e41-775cf2f9803b
	[COLOR=#AA22FF]echo[/COLOR]	[COLOR=#BB4444]'Chargement de Linux 2.6.32-43-generic ...'[/COLOR]
	linux	/boot/vmlinuz-2.6.32-43-generic [COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#B8860B]UUID[/COLOR][COLOR=#666666]=[/COLOR]4e7bef02-ca63-49d7-9e41-775cf2f9803b ro recovery nomodeset 
	[COLOR=#AA22FF]echo[/COLOR]	[COLOR=#BB4444]'Chargement du disque mémoire initial ...'[/COLOR]
	initrd	/boot/initrd.img-2.6.32-43-generic
[COLOR=#666666]}[/COLOR]
menuentry [COLOR=#BB4444]'Ubuntu, avec Linux 2.6.32-42-generic'[/COLOR] --class ubuntu --class gnu-linux --class gnu --class os [COLOR=#666666]{[/COLOR]
	recordfail
	gfxmode [COLOR=#B8860B]$linux_gfx_mode[/COLOR]
	insmod gzio
	insmod part_msdos
	insmod ext2
	[COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]'(hd0,msdos1)'[/COLOR]
	search --no-floppy --fs-uuid --set[COLOR=#666666]=[/COLOR]root 4e7bef02-ca63-49d7-9e41-775cf2f9803b
	linux	/boot/vmlinuz-2.6.32-42-generic [COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#B8860B]UUID[/COLOR][COLOR=#666666]=[/COLOR]4e7bef02-ca63-49d7-9e41-775cf2f9803b ro   quiet splash [COLOR=#B8860B]$vt_handoff[/COLOR]
	initrd	/boot/initrd.img-2.6.32-42-generic
[COLOR=#666666]}[/COLOR]
menuentry [COLOR=#BB4444]'Ubuntu, with Linux 2.6.32-42-generic (recovery mode)'[/COLOR] --class ubuntu --class gnu-linux --class gnu --class os [COLOR=#666666]{[/COLOR]
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	[COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]'(hd0,msdos1)'[/COLOR]
	search --no-floppy --fs-uuid --set[COLOR=#666666]=[/COLOR]root 4e7bef02-ca63-49d7-9e41-775cf2f9803b
	[COLOR=#AA22FF]echo[/COLOR]	[COLOR=#BB4444]'Chargement de Linux 2.6.32-42-generic ...'[/COLOR]
	linux	/boot/vmlinuz-2.6.32-42-generic [COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#B8860B]UUID[/COLOR][COLOR=#666666]=[/COLOR]4e7bef02-ca63-49d7-9e41-775cf2f9803b ro recovery nomodeset 
	[COLOR=#AA22FF]echo[/COLOR]	[COLOR=#BB4444]'Chargement du disque mémoire initial ...'[/COLOR]
	initrd	/boot/initrd.img-2.6.32-42-generic
[COLOR=#666666]}[/COLOR]
menuentry [COLOR=#BB4444]'Ubuntu, avec Linux 2.6.32-41-generic'[/COLOR] --class ubuntu --class gnu-linux --class gnu --class os [COLOR=#666666]{[/COLOR]
	recordfail
	gfxmode [COLOR=#B8860B]$linux_gfx_mode[/COLOR]
	insmod gzio
	insmod part_msdos
	insmod ext2
	[COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]'(hd0,msdos1)'[/COLOR]
	search --no-floppy --fs-uuid --set[COLOR=#666666]=[/COLOR]root 4e7bef02-ca63-49d7-9e41-775cf2f9803b
	linux	/boot/vmlinuz-2.6.32-41-generic [COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#B8860B]UUID[/COLOR][COLOR=#666666]=[/COLOR]4e7bef02-ca63-49d7-9e41-775cf2f9803b ro   quiet splash [COLOR=#B8860B]$vt_handoff[/COLOR]
	initrd	/boot/initrd.img-2.6.32-41-generic
[COLOR=#666666]}[/COLOR]
menuentry [COLOR=#BB4444]'Ubuntu, with Linux 2.6.32-41-generic (recovery mode)'[/COLOR] --class ubuntu --class gnu-linux --class gnu --class os [COLOR=#666666]{[/COLOR]
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	[COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]'(hd0,msdos1)'[/COLOR]
	search --no-floppy --fs-uuid --set[COLOR=#666666]=[/COLOR]root 4e7bef02-ca63-49d7-9e41-775cf2f9803b
	[COLOR=#AA22FF]echo[/COLOR]	[COLOR=#BB4444]'Chargement de Linux 2.6.32-41-generic ...'[/COLOR]
	linux	/boot/vmlinuz-2.6.32-41-generic [COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#B8860B]UUID[/COLOR][COLOR=#666666]=[/COLOR]4e7bef02-ca63-49d7-9e41-775cf2f9803b ro recovery nomodeset 
	[COLOR=#AA22FF]echo[/COLOR]	[COLOR=#BB4444]'Chargement du disque mémoire initial ...'[/COLOR]
	initrd	/boot/initrd.img-2.6.32-41-generic
[COLOR=#666666]}[/COLOR]
menuentry [COLOR=#BB4444]'Ubuntu, avec Linux 2.6.32-40-generic'[/COLOR] --class ubuntu --class gnu-linux --class gnu --class os [COLOR=#666666]{[/COLOR]
	recordfail
	gfxmode [COLOR=#B8860B]$linux_gfx_mode[/COLOR]
	insmod gzio
	insmod part_msdos
	insmod ext2
	[COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]'(hd0,msdos1)'[/COLOR]
	search --no-floppy --fs-uuid --set[COLOR=#666666]=[/COLOR]root 4e7bef02-ca63-49d7-9e41-775cf2f9803b
	linux	/boot/vmlinuz-2.6.32-40-generic [COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#B8860B]UUID[/COLOR][COLOR=#666666]=[/COLOR]4e7bef02-ca63-49d7-9e41-775cf2f9803b ro   quiet splash [COLOR=#B8860B]$vt_handoff[/COLOR]
	initrd	/boot/initrd.img-2.6.32-40-generic
[COLOR=#666666]}[/COLOR]
menuentry [COLOR=#BB4444]'Ubuntu, with Linux 2.6.32-40-generic (recovery mode)'[/COLOR] --class ubuntu --class gnu-linux --class gnu --class os [COLOR=#666666]{[/COLOR]
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	[COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]'(hd0,msdos1)'[/COLOR]
	search --no-floppy --fs-uuid --set[COLOR=#666666]=[/COLOR]root 4e7bef02-ca63-49d7-9e41-775cf2f9803b
	[COLOR=#AA22FF]echo[/COLOR]	[COLOR=#BB4444]'Chargement de Linux 2.6.32-40-generic ...'[/COLOR]
	linux	/boot/vmlinuz-2.6.32-40-generic [COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#B8860B]UUID[/COLOR][COLOR=#666666]=[/COLOR]4e7bef02-ca63-49d7-9e41-775cf2f9803b ro recovery nomodeset 
	[COLOR=#AA22FF]echo[/COLOR]	[COLOR=#BB4444]'Chargement du disque mémoire initial ...'[/COLOR]
	initrd	/boot/initrd.img-2.6.32-40-generic
[COLOR=#666666]}[/COLOR]
menuentry [COLOR=#BB4444]'Ubuntu, avec Linux 2.6.32-39-generic'[/COLOR] --class ubuntu --class gnu-linux --class gnu --class os [COLOR=#666666]{[/COLOR]
	recordfail
	gfxmode [COLOR=#B8860B]$linux_gfx_mode[/COLOR]
	insmod gzio
	insmod part_msdos
	insmod ext2
	[COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]'(hd0,msdos1)'[/COLOR]
	search --no-floppy --fs-uuid --set[COLOR=#666666]=[/COLOR]root 4e7bef02-ca63-49d7-9e41-775cf2f9803b
	linux	/boot/vmlinuz-2.6.32-39-generic [COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#B8860B]UUID[/COLOR][COLOR=#666666]=[/COLOR]4e7bef02-ca63-49d7-9e41-775cf2f9803b ro   quiet splash [COLOR=#B8860B]$vt_handoff[/COLOR]
	initrd	/boot/initrd.img-2.6.32-39-generic
[COLOR=#666666]}[/COLOR]
menuentry [COLOR=#BB4444]'Ubuntu, with Linux 2.6.32-39-generic (recovery mode)'[/COLOR] --class ubuntu --class gnu-linux --class gnu --class os [COLOR=#666666]{[/COLOR]
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	[COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]'(hd0,msdos1)'[/COLOR]
	search --no-floppy --fs-uuid --set[COLOR=#666666]=[/COLOR]root 4e7bef02-ca63-49d7-9e41-775cf2f9803b
	[COLOR=#AA22FF]echo[/COLOR]	[COLOR=#BB4444]'Chargement de Linux 2.6.32-39-generic ...'[/COLOR]
	linux	/boot/vmlinuz-2.6.32-39-generic [COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#B8860B]UUID[/COLOR][COLOR=#666666]=[/COLOR]4e7bef02-ca63-49d7-9e41-775cf2f9803b ro recovery nomodeset 
	[COLOR=#AA22FF]echo[/COLOR]	[COLOR=#BB4444]'Chargement du disque mémoire initial ...'[/COLOR]
	initrd	/boot/initrd.img-2.6.32-39-generic
[COLOR=#666666]}[/COLOR]
menuentry [COLOR=#BB4444]'Ubuntu, avec Linux 2.6.32-38-generic'[/COLOR] --class ubuntu --class gnu-linux --class gnu --class os [COLOR=#666666]{[/COLOR]
	recordfail
	gfxmode [COLOR=#B8860B]$linux_gfx_mode[/COLOR]
	insmod gzio
	insmod part_msdos
	insmod ext2
	[COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]'(hd0,msdos1)'[/COLOR]
	search --no-floppy --fs-uuid --set[COLOR=#666666]=[/COLOR]root 4e7bef02-ca63-49d7-9e41-775cf2f9803b
	linux	/boot/vmlinuz-2.6.32-38-generic [COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#B8860B]UUID[/COLOR][COLOR=#666666]=[/COLOR]4e7bef02-ca63-49d7-9e41-775cf2f9803b ro   quiet splash [COLOR=#B8860B]$vt_handoff[/COLOR]
	initrd	/boot/initrd.img-2.6.32-38-generic
[COLOR=#666666]}[/COLOR]
menuentry [COLOR=#BB4444]'Ubuntu, with Linux 2.6.32-38-generic (recovery mode)'[/COLOR] --class ubuntu --class gnu-linux --class gnu --class os [COLOR=#666666]{[/COLOR]
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	[COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]'(hd0,msdos1)'[/COLOR]
	search --no-floppy --fs-uuid --set[COLOR=#666666]=[/COLOR]root 4e7bef02-ca63-49d7-9e41-775cf2f9803b
	[COLOR=#AA22FF]echo[/COLOR]	[COLOR=#BB4444]'Chargement de Linux 2.6.32-38-generic ...'[/COLOR]
	linux	/boot/vmlinuz-2.6.32-38-generic [COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#B8860B]UUID[/COLOR][COLOR=#666666]=[/COLOR]4e7bef02-ca63-49d7-9e41-775cf2f9803b ro recovery nomodeset 
	[COLOR=#AA22FF]echo[/COLOR]	[COLOR=#BB4444]'Chargement du disque mémoire initial ...'[/COLOR]
	initrd	/boot/initrd.img-2.6.32-38-generic
[COLOR=#666666]}[/COLOR]
menuentry [COLOR=#BB4444]'Ubuntu, avec Linux 2.6.32-37-generic'[/COLOR] --class ubuntu --class gnu-linux --class gnu --class os [COLOR=#666666]{[/COLOR]
	recordfail
	gfxmode [COLOR=#B8860B]$linux_gfx_mode[/COLOR]
	insmod gzio
	insmod part_msdos
	insmod ext2
	[COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]'(hd0,msdos1)'[/COLOR]
	search --no-floppy --fs-uuid --set[COLOR=#666666]=[/COLOR]root 4e7bef02-ca63-49d7-9e41-775cf2f9803b
	linux	/boot/vmlinuz-2.6.32-37-generic [COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#B8860B]UUID[/COLOR][COLOR=#666666]=[/COLOR]4e7bef02-ca63-49d7-9e41-775cf2f9803b ro   quiet splash [COLOR=#B8860B]$vt_handoff[/COLOR]
	initrd	/boot/initrd.img-2.6.32-37-generic
[COLOR=#666666]}[/COLOR]
menuentry [COLOR=#BB4444]'Ubuntu, with Linux 2.6.32-37-generic (recovery mode)'[/COLOR] --class ubuntu --class gnu-linux --class gnu --class os [COLOR=#666666]{[/COLOR]
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	[COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]'(hd0,msdos1)'[/COLOR]
	search --no-floppy --fs-uuid --set[COLOR=#666666]=[/COLOR]root 4e7bef02-ca63-49d7-9e41-775cf2f9803b
	[COLOR=#AA22FF]echo[/COLOR]	[COLOR=#BB4444]'Chargement de Linux 2.6.32-37-generic ...'[/COLOR]
	linux	/boot/vmlinuz-2.6.32-37-generic [COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#B8860B]UUID[/COLOR][COLOR=#666666]=[/COLOR]4e7bef02-ca63-49d7-9e41-775cf2f9803b ro recovery nomodeset 
	[COLOR=#AA22FF]echo[/COLOR]	[COLOR=#BB4444]'Chargement du disque mémoire initial ...'[/COLOR]
	initrd	/boot/initrd.img-2.6.32-37-generic
[COLOR=#666666]}[/COLOR]
menuentry [COLOR=#BB4444]'Ubuntu, avec Linux 2.6.32-33-generic'[/COLOR] --class ubuntu --class gnu-linux --class gnu --class os [COLOR=#666666]{[/COLOR]
	recordfail
	gfxmode [COLOR=#B8860B]$linux_gfx_mode[/COLOR]
	insmod gzio
	insmod part_msdos
	insmod ext2
	[COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]'(hd0,msdos1)'[/COLOR]
	search --no-floppy --fs-uuid --set[COLOR=#666666]=[/COLOR]root 4e7bef02-ca63-49d7-9e41-775cf2f9803b
	linux	/boot/vmlinuz-2.6.32-33-generic [COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#B8860B]UUID[/COLOR][COLOR=#666666]=[/COLOR]4e7bef02-ca63-49d7-9e41-775cf2f9803b ro   quiet splash [COLOR=#B8860B]$vt_handoff[/COLOR]
	initrd	/boot/initrd.img-2.6.32-33-generic
[COLOR=#666666]}[/COLOR]
menuentry [COLOR=#BB4444]'Ubuntu, with Linux 2.6.32-33-generic (recovery mode)'[/COLOR] --class ubuntu --class gnu-linux --class gnu --class os [COLOR=#666666]{[/COLOR]
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	[COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]'(hd0,msdos1)'[/COLOR]
	search --no-floppy --fs-uuid --set[COLOR=#666666]=[/COLOR]root 4e7bef02-ca63-49d7-9e41-775cf2f9803b
	[COLOR=#AA22FF]echo[/COLOR]	[COLOR=#BB4444]'Chargement de Linux 2.6.32-33-generic ...'[/COLOR]
	linux	/boot/vmlinuz-2.6.32-33-generic [COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#B8860B]UUID[/COLOR][COLOR=#666666]=[/COLOR]4e7bef02-ca63-49d7-9e41-775cf2f9803b ro recovery nomodeset 
	[COLOR=#AA22FF]echo[/COLOR]	[COLOR=#BB4444]'Chargement du disque mémoire initial ...'[/COLOR]
	initrd	/boot/initrd.img-2.6.32-33-generic
[COLOR=#666666]}[/COLOR]
[COLOR=#666666]}[/COLOR]
[COLOR=#008800]*### END /etc/grub.d/10_linux ###*[/COLOR]

[COLOR=#008800]*### BEGIN /etc/grub.d/20_linux_xen ###*[/COLOR]
[COLOR=#008800]*### END /etc/grub.d/20_linux_xen ###*[/COLOR]

[COLOR=#008800]*### BEGIN /etc/grub.d/20_memtest86+ ###*[/COLOR]
menuentry [COLOR=#BB4444]"Memory test (memtest86+)"[/COLOR] [COLOR=#666666]{[/COLOR]
	insmod part_msdos
	insmod ext2
	[COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]'(hd0,msdos1)'[/COLOR]
	search --no-floppy --fs-uuid --set[COLOR=#666666]=[/COLOR]root 4e7bef02-ca63-49d7-9e41-775cf2f9803b
	linux16	/boot/memtest86+.bin
[COLOR=#666666]}[/COLOR]
menuentry [COLOR=#BB4444]"Memory test (memtest86+, serial console 115200)"[/COLOR] [COLOR=#666666]{[/COLOR]
	insmod part_msdos
	insmod ext2
	[COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]'(hd0,msdos1)'[/COLOR]
	search --no-floppy --fs-uuid --set[COLOR=#666666]=[/COLOR]root 4e7bef02-ca63-49d7-9e41-775cf2f9803b
	linux16	/boot/memtest86+.bin [COLOR=#B8860B]console[/COLOR][COLOR=#666666]=[/COLOR]ttyS0,115200n8
[COLOR=#666666]}[/COLOR]
[COLOR=#008800]*### END /etc/grub.d/20_memtest86+ ###*[/COLOR]

[COLOR=#008800]*### BEGIN /etc/grub.d/30_os-prober ###*[/COLOR]
[COLOR=#008800]*### END /etc/grub.d/30_os-prober ###*[/COLOR]

[COLOR=#008800]*### BEGIN /etc/grub.d/30_uefi-firmware ###*[/COLOR]
[COLOR=#008800]*### END /etc/grub.d/30_uefi-firmware ###*[/COLOR]

[COLOR=#008800]*### BEGIN /etc/grub.d/40_custom ###*[/COLOR]
[COLOR=#008800]*# This file provides an easy way to add custom menu entries.  Simply type the*[/COLOR]
[COLOR=#008800]*# menu entries you want to add after this comment.  Be careful not to change*[/COLOR]
[COLOR=#008800]*# the 'exec tail' line above.*[/COLOR]
[COLOR=#008800]*### END /etc/grub.d/40_custom ###*[/COLOR]

[COLOR=#008800]*### BEGIN /etc/grub.d/41_custom ###*[/COLOR]
[COLOR=#AA22FF]**if**[/COLOR] [COLOR=#666666][[/COLOR] -f  [COLOR=#B8860B]$prefix[/COLOR]/custom.cfg [COLOR=#666666]][/COLOR]; [COLOR=#AA22FF]**then**[/COLOR]
[COLOR=#AA22FF]**  **[/COLOR][COLOR=#AA22FF]source[/COLOR] [COLOR=#B8860B]$prefix[/COLOR]/custom.cfg;
[COLOR=#AA22FF]**fi**[/COLOR]
[COLOR=#008800]*### END /etc/grub.d/41_custom ###*[/COLOR]
--------------------------------------------------------------------------------

[COLOR=#666666]===============================[/COLOR] sda1/etc/fstab: [COLOR=#666666]================================[/COLOR]

--------------------------------------------------------------------------------
[COLOR=#008800]*# /etc/fstab: static file system information.*[/COLOR]
[COLOR=#008800]*#*[/COLOR]
[COLOR=#008800]*# Use 'blkid -o value -s UUID' to print the universally unique identifier*[/COLOR]
[COLOR=#008800]*# for a device; this may be used with UUID= as a more robust way to name*[/COLOR]
[COLOR=#008800]*# devices that works even if disks are added and removed. See fstab(5).*[/COLOR]
[COLOR=#008800]*#*[/COLOR]
[COLOR=#008800]*# <file system> <mount point>   <type>  <options>       <dump>  <pass>*[/COLOR]
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda1       /               ext4    [COLOR=#B8860B]errors[/COLOR][COLOR=#666666]=[/COLOR]remount-ro 0       1
/dev/sda6       /home           ext4    defaults,user_xattr        0       2
/dev/sdb1       /media/Stockage ext4    defaults        0       2
[COLOR=#008800]*# swap was on /dev/sda5 during installation*[/COLOR]
[COLOR=#B8860B]UUID[/COLOR][COLOR=#666666]=[/COLOR]2021d5eb-6df5-49b0-ab3d-2bd348e04335 none            swap    sw              0       0
--------------------------------------------------------------------------------

[COLOR=#666666]===================[/COLOR] sda1: Location of files loaded by Grub: [COLOR=#666666]====================[/COLOR]

           GiB - GB             File                                 Fragment[COLOR=#666666]([/COLOR]s[COLOR=#666666])[/COLOR]

   8.188140869 [COLOR=#666666]=[/COLOR] 8.791949312    boot/grub/grub.cfg                             1
  36.435485840 [COLOR=#666666]=[/COLOR] 39.122305024   boot/grub/core.img                             1
   8.163013458 [COLOR=#666666]=[/COLOR] 8.764968960    boot/vmlinuz-2.6.32-33-generic                 1
   8.254753113 [COLOR=#666666]=[/COLOR] 8.863473664    boot/vmlinuz-2.6.32-37-generic                 1
   8.274131775 [COLOR=#666666]=[/COLOR] 8.884281344    boot/vmlinuz-2.6.32-38-generic                 1
   8.379760742 [COLOR=#666666]=[/COLOR] 8.997699584    boot/vmlinuz-2.6.32-39-generic                 1
   8.385559082 [COLOR=#666666]=[/COLOR] 9.003925504    boot/vmlinuz-2.6.32-40-generic                 1
   8.504764557 [COLOR=#666666]=[/COLOR] 9.131921408    boot/vmlinuz-2.6.32-41-generic                 1
   8.411972046 [COLOR=#666666]=[/COLOR] 9.032286208    boot/vmlinuz-2.6.32-42-generic                 1
   8.417774200 [COLOR=#666666]=[/COLOR] 9.038516224    boot/vmlinuz-2.6.32-43-generic                 1
  41.102420807 [COLOR=#666666]=[/COLOR] 44.133388288   boot/vmlinuz-2.6.32-44-generic                 1
  46.200077057 [COLOR=#666666]=[/COLOR] 49.606955008   boot/vmlinuz-2.6.32-45-generic                 1
  21.200077057 [COLOR=#666666]=[/COLOR] 22.763409408   boot/vmlinuz-2.6.32-46-generic                 2
  37.491092682 [COLOR=#666666]=[/COLOR] 40.255754240   boot/vmlinuz-2.6.32-47-generic                 1
   5.126705170 [COLOR=#666666]=[/COLOR] 5.504757760    boot/vmlinuz-3.2.0-43-generic                  1
  40.712642670 [COLOR=#666666]=[/COLOR] 43.714867200   boot/vmlinuz-3.2.0-44-generic                  2
  42.443111420 [COLOR=#666666]=[/COLOR] 45.572943872   boot/vmlinuz-3.2.0-45-generic                  1
   0.579101562 [COLOR=#666666]=[/COLOR] 0.621805568    boot/vmlinuz-3.2.0-48-generic                  2
   7.923583984 [COLOR=#666666]=[/COLOR] 8.507883520    boot/vmlinuz-3.2.0-49-generic                  2
  13.333740234 [COLOR=#666666]=[/COLOR] 14.316994560   boot/vmlinuz-3.2.0-51-generic                  1
  37.677490234 [COLOR=#666666]=[/COLOR] 40.455897088   boot/vmlinuz-3.2.0-52-generic                  2
   3.716552734 [COLOR=#666666]=[/COLOR] 3.990618112    boot/vmlinuz-3.2.0-53-generic                  1
  11.525146484 [COLOR=#666666]=[/COLOR] 12.375031808   boot/vmlinuz-3.2.0-54-generic                  1
  18.892337799 [COLOR=#666666]=[/COLOR] 20.285493248   boot/vmlinuz-3.2.0-55-generic                  1
  20.786869049 [COLOR=#666666]=[/COLOR] 22.319730688   boot/vmlinuz-3.2.0-56-generic                  2
  39.458744049 [COLOR=#666666]=[/COLOR] 42.368503808   boot/vmlinuz-3.2.0-57-generic                  1
  11.509525299 [COLOR=#666666]=[/COLOR] 12.358258688   boot/vmlinuz-3.2.0-58-generic                  2
  10.611087799 [COLOR=#666666]=[/COLOR] 11.393568768   boot/vmlinuz-3.2.0-59-generic                  2
  19.060497284 [COLOR=#666666]=[/COLOR] 20.466053120   boot/vmlinuz-3.5.0-18-generic                  2
  19.060497284 [COLOR=#666666]=[/COLOR] 20.466053120   vmlinuz                                        2
  19.060497284 [COLOR=#666666]=[/COLOR] 20.466053120   vmlinuz.old                                    2
   8.178344727 [COLOR=#666666]=[/COLOR] 8.781430784    boot/initrd.img-2.6.32-33-generic              1
   8.270347595 [COLOR=#666666]=[/COLOR] 8.880218112    boot/initrd.img-2.6.32-37-generic              1
   2.676742554 [COLOR=#666666]=[/COLOR] 2.874130432    boot/initrd.img-2.6.32-38-generic              2
   8.395370483 [COLOR=#666666]=[/COLOR] 9.014460416    boot/initrd.img-2.6.32-39-generic              1
   8.403167725 [COLOR=#666666]=[/COLOR] 9.022832640    boot/initrd.img-2.6.32-40-generic              1
   8.618148804 [COLOR=#666666]=[/COLOR] 9.253666816    boot/initrd.img-2.6.32-41-generic              1
   8.625949860 [COLOR=#666666]=[/COLOR] 9.262043136    boot/initrd.img-2.6.32-42-generic              1
  32.208007812 [COLOR=#666666]=[/COLOR] 34.583085056   boot/initrd.img-2.6.32-43-generic              2
   8.512573242 [COLOR=#666666]=[/COLOR] 9.140305920    boot/initrd.img-2.6.32-44-generic              1
   8.459884644 [COLOR=#666666]=[/COLOR] 9.083731968    boot/initrd.img-2.6.32-45-generic              1
   8.929470062 [COLOR=#666666]=[/COLOR] 9.587945472    boot/initrd.img-2.6.32-46-generic              2
   4.922851562 [COLOR=#666666]=[/COLOR] 5.285871616    boot/initrd.img-2.6.32-47-generic              2
  40.858947754 [COLOR=#666666]=[/COLOR] 43.871961088   boot/initrd.img-3.2.0-43-generic               3
  41.665039062 [COLOR=#666666]=[/COLOR] 44.737495040   boot/initrd.img-3.2.0-44-generic               2
  42.056777954 [COLOR=#666666]=[/COLOR] 45.158121472   boot/initrd.img-3.2.0-45-generic               2
   2.912303925 [COLOR=#666666]=[/COLOR] 3.127062528    boot/initrd.img-3.2.0-48-generic               3
   1.191963196 [COLOR=#666666]=[/COLOR] 1.279860736    boot/initrd.img-3.2.0-49-generic               2
  16.985351562 [COLOR=#666666]=[/COLOR] 18.237882368   boot/initrd.img-3.2.0-51-generic               2
   3.676338196 [COLOR=#666666]=[/COLOR] 3.947438080    boot/initrd.img-3.2.0-52-generic               1
   6.074241638 [COLOR=#666666]=[/COLOR] 6.522167296    boot/initrd.img-3.2.0-53-generic               2
  14.098213196 [COLOR=#666666]=[/COLOR] 15.137841152   boot/initrd.img-3.2.0-54-generic               2
  19.504467010 [COLOR=#666666]=[/COLOR] 20.942761984   boot/initrd.img-3.2.0-55-generic               2
  23.091506958 [COLOR=#666666]=[/COLOR] 24.794316800   boot/initrd.img-3.2.0-56-generic               3
  37.273826599 [COLOR=#666666]=[/COLOR] 40.022466560   boot/initrd.img-3.2.0-57-generic               2
  15.199810028 [COLOR=#666666]=[/COLOR] 16.320671744   boot/initrd.img-3.2.0-58-generic               2
  19.024414062 [COLOR=#666666]=[/COLOR] 20.427309056   boot/initrd.img-3.2.0-59-generic               3
  20.466892242 [COLOR=#666666]=[/COLOR] 21.976158208   boot/initrd.img-3.5.0-18-generic               2
  20.466892242 [COLOR=#666666]=[/COLOR] 21.976158208   initrd.img                                     [COLOR=#B8860B]2[/COLOR]

[COLOR=#666666]========================[/COLOR] Unknown MBRs/Boot Sectors/etc: [COLOR=#666666]========================[/COLOR]

Unknown BootLoader on sda2

00000000  70 ec c1 16 7d f8 c1 19  52 a6 c1 1e b9 bd c1 26  |p...[COLOR=#666666]}[/COLOR]...R......&|
00000010  22 f7 c1 2e c2 46 c1 37  cc a9 c1 40 85 8b c1 48  |[COLOR=#BB4444]"....F.7...@...H|[/COLOR]
[COLOR=#BB4444]00000020  56 81 c1 4e be 3a c1 53  4d f1 c1 55 89 da c1 54  |V..N.:.SM..U...T|[/COLOR]
[COLOR=#BB4444]00000030  e2 39 c1 50 a3 e1 c1 48  11 af c1 3a 70 98 c1 27  |.9.P...H...:p..'|[/COLOR]
[COLOR=#BB4444]00000040  31 98 c1 0e 0c e2 c0 de  39 d0 c0 95 e7 83 c0 0a  |1.......9.......|[/COLOR]
[COLOR=#BB4444]00000050  48 4e 3f 09 88 32 40 53  42 6a 40 c0 5c 9a 41 08  |HN?..2@SBj@.\.A.|[/COLOR]
[COLOR=#BB4444]00000060  c4 b6 41 2c c3 4f 41 4a  a4 62 41 61 46 cd 41 70  |..A,.OAJ.bAaF.Ap|[/COLOR]
[COLOR=#BB4444]00000070  06 b6 41 76 d3 c1 41 76  33 c9 41 6f 39 b2 41 63  |..Av..Av3.Ao9.Ac|[/COLOR]
[COLOR=#BB4444]00000080  79 d7 41 54 e3 fa 41 45  97 2d 41 37 b8 10 41 2d  |y.AT..AE.-A7..A-|[/COLOR]
[COLOR=#BB4444]00000090  33 29 41 27 91 70 41 27  d1 da 41 2e 5c cc 41 3b  |3)A'.pA'..A.\.A;|[/COLOR]
[COLOR=#BB4444]000000a0  00 f5 41 4c fe a3 41 63  43 0e 41 7c 7c d4 41 8b  |..AL..AcC.A||.A.|[/COLOR]
[COLOR=#BB4444]000000b0  aa 35 41 99 4e aa 41 a6  aa d1 41 b3 63 bb 41 bf  |.5A.N.A...A.c.A.|[/COLOR]
[COLOR=#BB4444]000000c0  3e 91 41 ca 17 09 41 d3  d8 ad 41 dc 75 9b 41 e3  |>.A...A...A.u.A.|[/COLOR]
[COLOR=#BB4444]000000d0  e1 45 41 ea 0e 4d 41 ee  f0 ad 41 f2 83 7b 41 f4  |.EA..MA...A..{A.|[/COLOR]
[COLOR=#BB4444]000000e0  cf 19 41 f5 e9 f0 41 f5  fd f8 41 f5 3e fb 41 f3  |..A...A...A.>.A.|[/COLOR]
[COLOR=#BB4444]000000f0  ea 52 41 f2 35 a0 41 f0  43 e5 41 ee 19 7b 41 eb  |.RA.5.A.C.A..{A.|[/COLOR]
[COLOR=#BB4444]00000100  95 4b 41 e8 65 1f 41 e4  0e c2 41 dd f2 02 41 d5  |.KA.e.A...A...A.|[/COLOR]
[COLOR=#BB4444]00000110  5c 32 41 c9 96 fd 41 ba  03 78 41 a6 2f bf 41 8d  |\2A...A..xA./.A.|[/COLOR]
[COLOR=#BB4444]00000120  e1 d8 41 62 6a 1c 41 21  1a 96 40 b2 ad 8a 3f 4f  |..Abj.A!..@...?O|[/COLOR]
[COLOR=#BB4444]00000130  c8 17 c0 82 d1 58 c1 0f  70 9b c1 5a 2e 87 c1 8f  |.....X..p..Z....|[/COLOR]
[COLOR=#BB4444]00000140  ba 61 c1 ae 50 0a c1 c8  34 d9 c1 dc 73 72 c1 eb  |.a..P...4...sr..|[/COLOR]
[COLOR=#BB4444]00000150  0b 99 c1 f3 61 0c c1 f6  18 c5 c1 f2 c2 1f c1 ea  |....a...........|[/COLOR]
[COLOR=#BB4444]00000160  86 c9 c1 dc e5 ec c1 cb  70 df c1 b5 69 47 c1 9c  |........p...iG..|[/COLOR]
[COLOR=#BB4444]00000170  c0 d1 c1 80 6c ab c1 45  ac f1 c1 05 40 d8 c0 8b  |....l..E....@...|[/COLOR]
[COLOR=#BB4444]00000180  3e 68 be 4b e1 ff 40 6a  01 38 40 f1 6c 6a 41 2d  |>h.K..@j.8@.ljA-|[/COLOR]
[COLOR=#BB4444]00000190  e7 a3 41 62 ce cf 41 85  4e a2 41 9a 6d 81 41 a6  |..Ab..A.N.A.m.A.|[/COLOR]
[COLOR=#BB4444]000001a0  bf b8 41 b7 fe 0c 41 ba  b8 3d 41 c6 2b 0b 41 b1  |..A...A..=A.+.A.|[/COLOR]
[COLOR=#BB4444]000001b0  5f 5d 41 a5 d0 62 42 29  2a fe 00 00 00 00 00 fe  |_]A..bB)*.......|[/COLOR]
[COLOR=#BB4444]000001c0  ff ff 82 fe ff ff 02 00  00 00 00 08 7a 00 00 fe  |............z...|[/COLOR]
[COLOR=#BB4444]000001d0  ff ff 05 fe ff ff 02 08  7a 00 00 28 ec 33 00 00  |........z..(.3..|[/COLOR]
[COLOR=#BB4444]000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|[/COLOR]
[COLOR=#BB4444]000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|[/COLOR]
[COLOR=#BB4444]00000200[/COLOR]


[COLOR=#BB4444]========= Devices which don't seem to have a corresponding hard drive: =========[/COLOR]

[COLOR=#BB4444]sdc sdd sde sdf sdg [/COLOR]


[COLOR=#BB4444]ADDITIONAL INFORMATION :[/COLOR]
[COLOR=#BB4444]=================== log of boot-repair 2014-04-10__10h57 ===================[/COLOR]
[COLOR=#BB4444]boot-repair version : 3.199~ppa40~precise[/COLOR]
[COLOR=#BB4444]boot-sav version : 3.199~ppa40~precise[/COLOR]
[COLOR=#BB4444]glade2script version : 3.2.2~ppa45~precise[/COLOR]
[COLOR=#BB4444]boot-sav-extra version : 3.199~ppa40~precise[/COLOR]
[COLOR=#BB4444]boot-repair est exécuté en session live (Ubuntu 12.04 LTS, precise, Ubuntu-fr, x86_64)[/COLOR]
[COLOR=#BB4444]ls: impossible d'accéder à /home/usr/.config: Aucun fichier ou dossier de ce type[/COLOR]
[COLOR=#BB4444]CPU op-mode(s):        32-bit, 64-bit[/COLOR]
[COLOR=#BB4444]file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.lz quiet splash -- debian-installer/language=fr keyboard-configuration/layoutcode?=fr keyboard-configuration/variantcode?=oss maybe-ubiquity[/COLOR]

[COLOR=#BB4444]=================== os-prober:[/COLOR]
[COLOR=#BB4444]/dev/sda1:Ubuntu 12.04.4 LTS (12.04):Ubuntu:linux[/COLOR]

[COLOR=#BB4444]=================== blkid:[/COLOR]
[COLOR=#BB4444]/dev/loop0: TYPE="[/COLOR]squashfs[COLOR=#BB4444]"[/COLOR]
[COLOR=#BB4444]/dev/sda1: UUID="[/COLOR]4e7bef02-ca63-49d7-9e41-775cf2f9803b[COLOR=#BB4444]" TYPE="[/COLOR]ext4[COLOR=#BB4444]"[/COLOR]
[COLOR=#BB4444]/dev/sda5: UUID="[/COLOR]2021d5eb-6df5-49b0-ab3d-2bd348e04335[COLOR=#BB4444]" TYPE="[/COLOR]swap[COLOR=#BB4444]"[/COLOR]
[COLOR=#BB4444]/dev/sda6: UUID="[/COLOR]39993f2b-d435-43ac-b137-5b39ac97472e[COLOR=#BB4444]" TYPE="[/COLOR]ext4[COLOR=#BB4444]"[/COLOR]
[COLOR=#BB4444]/dev/sr0: LABEL="[/COLOR]Ubuntu precise 20120425-15:29[COLOR=#BB4444]" TYPE="[/COLOR]iso9660[COLOR=#BB4444]"[/COLOR]
[COLOR=#BB4444]/dev/sdb1: UUID="[/COLOR]8722b4a4-435e-4848-bba6-45d3e8762f7d[COLOR=#BB4444]" TYPE="[/COLOR]ext4[COLOR=#BB4444]"[/COLOR]


[COLOR=#BB4444]1 disks with OS, 1 OS : 1 Linux, 0 MacOS, 0 Windows, 0 unknown type OS.[/COLOR]

[COLOR=#BB4444]Avertissement : la partition étendue ne débute pas sur une frontière de[/COLOR]
[COLOR=#BB4444]cylindres. DOS et Linux interpréteront les contenus différemment.[/COLOR]

[COLOR=#BB4444]=================== sda1/etc/grub.d/ :[/COLOR]
[COLOR=#BB4444]drwxr-xr-x  2 root     root     4096 févr.  6 21:02 grub.d[/COLOR]
[COLOR=#BB4444]total 60[/COLOR]
[COLOR=#BB4444]-rwxr-xr-x 1 root root 7806 déc.   6 10:06 00_header[/COLOR]
[COLOR=#BB4444]-rwxr-xr-x 1 root root 5522 janv. 22  2013 05_debian_theme[/COLOR]
[COLOR=#BB4444]-rwxr-xr-x 1 root root 7877 déc.   6 10:06 10_linux[/COLOR]
[COLOR=#BB4444]-rwxr-xr-x 1 root root 6449 déc.   6 10:06 20_linux_xen[/COLOR]
[COLOR=#BB4444]-rwxr-xr-x 1 root root 1588 nov.  27  2011 20_memtest86+[/COLOR]
[COLOR=#BB4444]-rwxr-xr-x 1 root root 6675 déc.   6 10:06 30_os-prober[/COLOR]
[COLOR=#BB4444]-rwxr-xr-x 1 root root 1388 janv. 22  2013 30_uefi-firmware[/COLOR]
[COLOR=#BB4444]-rwxr-xr-x 1 root root  214 avril 27  2011 40_custom[/COLOR]
[COLOR=#BB4444]-rwxr-xr-x 1 root root   95 janv. 22  2013 41_custom[/COLOR]
[COLOR=#BB4444]-rw-r--r-- 1 root root  483 avril 27  2011 README[/COLOR]




[COLOR=#BB4444]=================== sda1/etc/default/grub :[/COLOR]

[COLOR=#BB4444]# If you change this file, run 'update-grub' afterwards to update[/COLOR]
[COLOR=#BB4444]# /boot/grub/grub.cfg.[/COLOR]
[COLOR=#BB4444]# For full documentation of the options in this file, see:[/COLOR]
[COLOR=#BB4444]#   info -f grub -n 'Simple configuration'[/COLOR]

[COLOR=#BB4444]GRUB_DEFAULT=0[/COLOR]
[COLOR=#BB4444]GRUB_HIDDEN_TIMEOUT=0[/COLOR]
[COLOR=#BB4444]GRUB_HIDDEN_TIMEOUT_QUIET=true[/COLOR]
[COLOR=#BB4444]GRUB_TIMEOUT=10[/COLOR]
[COLOR=#BB4444]GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`[/COLOR]
[COLOR=#BB4444]GRUB_CMDLINE_LINUX_DEFAULT="[/COLOR]quiet splash[COLOR=#BB4444]"[/COLOR]
[COLOR=#BB4444]GRUB_CMDLINE_LINUX=""[/COLOR]

[COLOR=#BB4444]# Uncomment to enable BadRAM filtering, modify to suit your needs[/COLOR]
[COLOR=#BB4444]# This works with Linux (no patch required) and with any kernel that obtains[/COLOR]
[COLOR=#BB4444]# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)[/COLOR]
[COLOR=#BB4444]#GRUB_BADRAM="[/COLOR]0x01234567,0xfefefefe,0x89abcdef,0xefefefef[COLOR=#BB4444]"[/COLOR]

[COLOR=#BB4444]# Uncomment to disable graphical terminal (grub-pc only)[/COLOR]
[COLOR=#BB4444]#GRUB_TERMINAL=console[/COLOR]

[COLOR=#BB4444]# The resolution used on graphical terminal[/COLOR]
[COLOR=#BB4444]# note that you can use only modes which your graphic card supports via VBE[/COLOR]
[COLOR=#BB4444]# you can see them in real GRUB with the command `vbeinfo'[/COLOR]
[COLOR=#BB4444]#GRUB_GFXMODE=640x480[/COLOR]

[COLOR=#BB4444]# Uncomment if you don't want GRUB to pass "[/COLOR][COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#B8860B]UUID[/COLOR][COLOR=#666666]=[/COLOR]xxx[COLOR=#BB4444]" parameter to Linux[/COLOR]
[COLOR=#BB4444]#GRUB_DISABLE_LINUX_UUID=true[/COLOR]

[COLOR=#BB4444]# Uncomment to disable generation of recovery mode menu entries[/COLOR]
[COLOR=#BB4444]#GRUB_DISABLE_RECOVERY="[/COLOR][COLOR=#AA22FF]true[/COLOR][COLOR=#BB4444]"[/COLOR]

[COLOR=#BB4444]# Uncomment to get a beep at grub start[/COLOR]
[COLOR=#BB4444]#GRUB_INIT_TUNE="[/COLOR]480 440 1"




[COLOR=#666666]===================[/COLOR] [COLOR=#B8860B]sda1recordfail[/COLOR][COLOR=#666666]=[/COLOR]1/grub/grubenv :
[COLOR=#B8860B]recordfail[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#B8860B]1[/COLOR]



[COLOR=#666666]===================[/COLOR] UEFI/Legacy mode:
Le disque Ubuntu Edition Francophone ne peut pas être démarré en mode EFI.
SecureBoot maybe enabled.


[COLOR=#666666]===================[/COLOR] PARTITIONS & DISKS:
sda1	: sda,	not-sepboot,	grubenv-ng	grub2,	grub-pc ,	update-grub,	64,	with-boot,	is-os,	not--efi--part,	fstab-without-boot,	fstab-without-efi,	no-nt,	no-winload,	no-recov-nor-hid,	no-bmgr,	notwinboot,	apt-get,	grub-install,	with--usr,	fstab-without-usr,	not-sep-usr,	standard,	not-far,	/mnt/boot-sav/sda1.
sda6	: sda,	maybesepboot,	no-grubenv	nogrub,	no-docgrub,	no-update-grub,	32,	no-boot,	no-os,	not--efi--part,	part-has-no-fstab,	part-has-no-fstab,	no-nt,	no-winload,	no-recov-nor-hid,	no-bmgr,	notwinboot,	nopakmgr,	nogrubinstall,	no---usr,	part-has-no-fstab,	not-sep-usr,	standard,	farbios,	/mnt/boot-sav/sda6.
sdb1	: sdb,	maybesepboot,	no-grubenv	nogrub,	no-docgrub,	no-update-grub,	32,	no-boot,	no-os,	not--efi--part,	part-has-no-fstab,	part-has-no-fstab,	no-nt,	no-winload,	no-recov-nor-hid,	no-bmgr,	notwinboot,	nopakmgr,	nogrubinstall,	no---usr,	part-has-no-fstab,	not-sep-usr,	standard,	farbios,	/mnt/boot-sav/sdb1.

sda	: not-GPT,	BIOSboot-not-needed,	has-no-EFIpart, 	not-usb,	has-os,	2048 sectors * 512 bytes
sdb	: not-GPT,	BIOSboot-not-needed,	has-no-EFIpart, 	not-usb,	no-os,	2048 sectors * 512 [COLOR=#B8860B]bytes[/COLOR]


[COLOR=#666666]===================[/COLOR] parted -l:

Model: ATA MAXTOR STM350032 [COLOR=#666666]([/COLOR]scsi[COLOR=#666666])[/COLOR]
Disk /dev/sda: 500GB
Sector size [COLOR=#666666]([/COLOR]logical/physical[COLOR=#666666])[/COLOR]: 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
1      1049kB  50.0GB  50.0GB  primary   ext4            boot
2      50.0GB  500GB   450GB   extended
5      50.0GB  54.1GB  4095MB  logical   linux-swap[COLOR=#666666]([/COLOR]v1[COLOR=#666666])[/COLOR]
6      54.1GB  500GB   446GB   logical   ext4


Model: ATA MAXTOR STM350032 [COLOR=#666666]([/COLOR]scsi[COLOR=#666666])[/COLOR]
Disk /dev/sdb: 500GB
Sector size [COLOR=#666666]([/COLOR]logical/physical[COLOR=#666666])[/COLOR]: 512B/512B
Partition Table: msdos

Number  Start   End    Size   Type     File system  Flags
1      1049kB  500GB  500GB  primary  ext4



                                                                          
Error: Invalid partition table - recursive partition on /dev/sr0.

[COLOR=#666666]===================[/COLOR] parted -lm:

BYT;
/dev/sda:500GB:scsi:512:512:msdos:ATA MAXTOR STM350032;
1:1049kB:50.0GB:50.0GB:ext4::boot;
2:50.0GB:500GB:450GB:::;
5:50.0GB:54.1GB:4095MB:linux-swap[COLOR=#666666]([/COLOR]v1[COLOR=#666666])[/COLOR]::;
6:54.1GB:500GB:446GB:ext4::;

BYT;
/dev/sdb:500GB:scsi:512:512:msdos:ATA MAXTOR STM350032;
1:1049kB:500GB:500GB:ext4::;


                                                                          
Error: Invalid partition table - recursive partition on /dev/sr0.


[COLOR=#666666]===================[/COLOR] mount:
/cow on / [COLOR=#AA22FF]type [/COLOR]overlayfs [COLOR=#666666]([/COLOR]rw[COLOR=#666666])[/COLOR]
proc on /proc [COLOR=#AA22FF]type [/COLOR]proc [COLOR=#666666]([/COLOR]rw,noexec,nosuid,nodev[COLOR=#666666])[/COLOR]
sysfs on /sys [COLOR=#AA22FF]type [/COLOR]sysfs [COLOR=#666666]([/COLOR]rw,noexec,nosuid,nodev[COLOR=#666666])[/COLOR]
udev on /dev [COLOR=#AA22FF]type [/COLOR]devtmpfs [COLOR=#666666]([/COLOR]rw,mode[COLOR=#666666]=[/COLOR]0755[COLOR=#666666])[/COLOR]
devpts on /dev/pts [COLOR=#AA22FF]type [/COLOR]devpts [COLOR=#666666]([/COLOR]rw,noexec,nosuid,gid[COLOR=#666666]=[/COLOR]5,mode[COLOR=#666666]=[/COLOR]0620[COLOR=#666666])[/COLOR]
tmpfs on /run [COLOR=#AA22FF]type [/COLOR]tmpfs [COLOR=#666666]([/COLOR]rw,noexec,nosuid,size[COLOR=#666666]=[/COLOR]10%,mode[COLOR=#666666]=[/COLOR]0755[COLOR=#666666])[/COLOR]
/dev/sr0 on /cdrom [COLOR=#AA22FF]type [/COLOR]iso9660 [COLOR=#666666]([/COLOR]ro,noatime[COLOR=#666666])[/COLOR]
/dev/loop0 on /rofs [COLOR=#AA22FF]type [/COLOR]squashfs [COLOR=#666666]([/COLOR]ro,noatime[COLOR=#666666])[/COLOR]
none on /sys/fs/fuse/connections [COLOR=#AA22FF]type [/COLOR]fusectl [COLOR=#666666]([/COLOR]rw[COLOR=#666666])[/COLOR]
none on /sys/kernel/debug [COLOR=#AA22FF]type [/COLOR]debugfs [COLOR=#666666]([/COLOR]rw[COLOR=#666666])[/COLOR]
none on /sys/kernel/security [COLOR=#AA22FF]type [/COLOR]securityfs [COLOR=#666666]([/COLOR]rw[COLOR=#666666])[/COLOR]
tmpfs on /tmp [COLOR=#AA22FF]type [/COLOR]tmpfs [COLOR=#666666]([/COLOR]rw,nosuid,nodev[COLOR=#666666])[/COLOR]
none on /run/lock [COLOR=#AA22FF]type [/COLOR]tmpfs [COLOR=#666666]([/COLOR]rw,noexec,nosuid,nodev,size[COLOR=#666666]=[/COLOR]5242880[COLOR=#666666])[/COLOR]
none on /run/shm [COLOR=#AA22FF]type [/COLOR]tmpfs [COLOR=#666666]([/COLOR]rw,nosuid,nodev[COLOR=#666666])[/COLOR]
gvfs-fuse-daemon on /home/ubuntu/.gvfs [COLOR=#AA22FF]type [/COLOR]fuse.gvfs-fuse-daemon [COLOR=#666666]([/COLOR]rw,nosuid,nodev,user[COLOR=#666666]=[/COLOR]ubuntu[COLOR=#666666])[/COLOR]
/dev/sda1 on /mnt/boot-sav/sda1 [COLOR=#AA22FF]type [/COLOR]ext4 [COLOR=#666666]([/COLOR]rw[COLOR=#666666])[/COLOR]
/dev/sda6 on /mnt/boot-sav/sda6 [COLOR=#AA22FF]type [/COLOR]ext4 [COLOR=#666666]([/COLOR]rw[COLOR=#666666])[/COLOR]
/dev/sdb1 on /mnt/boot-sav/sdb1 [COLOR=#AA22FF]type [/COLOR]ext4 [COLOR=#666666]([/COLOR]rw[COLOR=#666666])[/COLOR]


[COLOR=#666666]===================[/COLOR] ls:
/sys/block/sda [COLOR=#666666]([/COLOR]filtered[COLOR=#666666])[/COLOR]:  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sda1 sda2 sda5 sda6 size slaves stat subsystem trace uevent
/sys/block/sdb [COLOR=#666666]([/COLOR]filtered[COLOR=#666666])[/COLOR]:  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sdb1 size slaves stat subsystem trace uevent
/sys/block/sdc [COLOR=#666666]([/COLOR]filtered[COLOR=#666666])[/COLOR]:  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/sys/block/sdd [COLOR=#666666]([/COLOR]filtered[COLOR=#666666])[/COLOR]:  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/sys/block/sde [COLOR=#666666]([/COLOR]filtered[COLOR=#666666])[/COLOR]:  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/sys/block/sdf [COLOR=#666666]([/COLOR]filtered[COLOR=#666666])[/COLOR]:  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/sys/block/sdg [COLOR=#666666]([/COLOR]filtered[COLOR=#666666])[/COLOR]:  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/sys/block/sr0 [COLOR=#666666]([/COLOR]filtered[COLOR=#666666])[/COLOR]:  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/dev [COLOR=#666666]([/COLOR]filtered[COLOR=#666666])[/COLOR]:  autofs block bsg btrfs-control bus cdrom cdrw char console core cpu cpu_dma_latency disk dri dvd dvdrw ecryptfs fb0 fd full fuse hidraw0 hpet input kmsg log mapper mcelog mem net network_latency network_throughput null oldmem port ppp psaux ptmx pts random rfkill rtc rtc0 sda sda1 sda2 sda5 sda6 sdb sdb1 sdc sdd sde sdf sdg sg0 sg1 sg2 sg3 sg4 sg5 sg6 sg7 shm snapshot snd sr0 stderr stdin stdout uinput urandom usb usbmon0 usbmon1 usbmon2 usbmon3 usbmon4 usbmon5 usbmon6 usbmon7 usbmon8 vga_arbiter zero
ls /dev/mapper:  [COLOR=#B8860B]control[/COLOR]

[COLOR=#666666]===================[/COLOR] df -Th:

Filesystem     Type       Size  Used Avail Use% Mounted on
/cow           overlayfs  2.0G  131M  1.9G   7% /
udev           devtmpfs   2.0G   12K  2.0G   1% /dev
tmpfs          tmpfs      791M  816K  791M   1% /run
/dev/sr0       iso9660    668M  668M     0 100% /cdrom
/dev/loop0     squashfs   647M  647M     0 100% /rofs
tmpfs          tmpfs      2.0G   28K  2.0G   1% /tmp
none           tmpfs      5.0M  4.0K  5.0M   1% /run/lock
none           tmpfs      2.0G   76K  2.0G   1% /run/shm
/dev/sda1      ext4        47G   19G   26G  42% /mnt/boot-sav/sda1
/dev/sda6      ext4       415G  392G  2.5G 100% /mnt/boot-sav/sda6
/dev/sdb1      ext4       466G  397G   46G  90% /mnt/boot-sav/sdb1

[COLOR=#666666]===================[/COLOR] fdisk -l:

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
[COLOR=#B8860B]Units[/COLOR] [COLOR=#666666]=[/COLOR] sectors of 1 * [COLOR=#B8860B]512[/COLOR] [COLOR=#666666]=[/COLOR] 512 bytes
Sector size [COLOR=#666666]([/COLOR]logical/physical[COLOR=#666666])[/COLOR]: 512 bytes / 512 bytes
I/O size [COLOR=#666666]([/COLOR]minimum/optimal[COLOR=#666666])[/COLOR]: 512 bytes / 512 bytes
Disk identifier: 0x000c4724

Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048    97656831    48827392   83  Linux
/dev/sda2        97658878   976771071   439556097    5  Extended
/dev/sda5        97658880   105656319     3998720   82  Linux swap / Solaris
/dev/sda6       105658368   976771071   435556352   83  Linux

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
[COLOR=#B8860B]Units[/COLOR] [COLOR=#666666]=[/COLOR] sectors of 1 * [COLOR=#B8860B]512[/COLOR] [COLOR=#666666]=[/COLOR] 512 bytes
Sector size [COLOR=#666666]([/COLOR]logical/physical[COLOR=#666666])[/COLOR]: 512 bytes / 512 bytes
I/O size [COLOR=#666666]([/COLOR]minimum/optimal[COLOR=#666666])[/COLOR]: 512 bytes / 512 bytes
Disk identifier: 0x0001cb17

Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048   976771071   488384512   83  [COLOR=#B8860B]Linux[/COLOR]



[COLOR=#666666]===================[/COLOR] Recommended repair
Recommended-Repair
This setting will reinstall the grub2 of sda1 into the MBRs of all disks [COLOR=#666666]([/COLOR]except USB without OS[COLOR=#666666])[/COLOR].
The boot flag will be placed on sdb1.
Additional repair will be performed: unhide-bootmenu-10s


parted /dev/sdb [COLOR=#AA22FF]set [/COLOR]1 boot on

                                                                          
Information: Ne pas oublier de mettre à jour /etc/fstab si nécessaire.

Unhide GRUB boot menu in sda1/etc/default/grub

Reinstall the GRUB of sda1 into all MBRs of disks with OS or not-USB

*******lspci -nnk | grep -iA3 vga
01:00.0 VGA compatible controller [COLOR=#666666][[/COLOR]0300[COLOR=#666666]][/COLOR]: NVIDIA Corporation G94 [COLOR=#666666][[/COLOR]GeForce 9600 GT[COLOR=#666666]][/COLOR] [COLOR=#666666][[/COLOR]10de:0622[COLOR=#666666]][/COLOR] [COLOR=#666666]([/COLOR]rev a1[COLOR=#666666])[/COLOR]
Subsystem: ASUSTeK Computer Inc. Device [COLOR=#666666][[/COLOR]1043:82a1[COLOR=#666666]][/COLOR]
Kernel driver in use: nouveau
02:00.0 Ethernet controller [COLOR=#666666][[/COLOR]0200[COLOR=#666666]][/COLOR]: Qualcomm Atheros AR8121/AR8113/AR8114 Gigabit or Fast Ethernet [COLOR=#666666][[/COLOR]1969:1026[COLOR=#666666]][/COLOR] [COLOR=#666666]([/COLOR]rev b0[COLOR=#666666])[/COLOR]
*******

chroot: impossible d[COLOR=#BB4444]'exécuter la commande «grub-install»: Erreur d'[/COLOR]entrée/sortie
,.

Reinstall the GRUB of sda1 into the MBR of sdb
chroot: failed to run [COLOR=#AA22FF]command[/COLOR] [COLOR=#BB4444]`[/COLOR]grub-install[COLOR=#BB4444]': Input/output error[/COLOR]
[COLOR=#BB4444]grub-install /dev/sdb: exit code of grub-install /dev/sdb:126[/COLOR]

[COLOR=#BB4444]*******lspci -nnk | grep -iA3 vga[/COLOR]
[COLOR=#BB4444]01:00.0 VGA compatible controller [0300]: NVIDIA Corporation G94 [GeForce 9600 GT] [10de:0622] (rev a1)[/COLOR]
[COLOR=#BB4444]Subsystem: ASUSTeK Computer Inc. Device [1043:82a1][/COLOR]
[COLOR=#BB4444]Kernel driver in use: nouveau[/COLOR]
[COLOR=#BB4444]02:00.0 Ethernet controller [0200]: Qualcomm Atheros AR8121/AR8113/AR8114 Gigabit or Fast Ethernet [1969:1026] (rev b0)[/COLOR]
[COLOR=#BB4444]*******[/COLOR]

[COLOR=#BB4444]chroot: impossible d'[/COLOR]exécuter la commande «grub-install»: Erreur d[COLOR=#BB4444]'entrée/sortie[/COLOR]
[COLOR=#BB4444],.[/COLOR]

[COLOR=#BB4444]Reinstall the GRUB of sda1 into the MBR of sda[/COLOR]
[COLOR=#BB4444]chroot: failed to run command `grub-install'[/COLOR]: Input/output error
grub-install /dev/sda: [COLOR=#AA22FF]exit [/COLOR]code of grub-install /dev/sda:126
Failed to run [COLOR=#AA22FF]command [/COLOR]grub-install detected.
chroot: impossible d[COLOR=#BB4444]'exécuter la commande «type»: Aucun fichier ou dossier de ce type[/COLOR]
[COLOR=#BB4444]lrwxrwxrwx 1 root root 32 déc.   6 10:07 /mnt/boot-sav/sda1/usr/sbin/grub-install -> ../lib/grub/i386-pc/grub-install[/COLOR]
[COLOR=#BB4444]lrwxrwxrwx 1 root root 32 déc.   6 10:07 /mnt/boot-sav/sda1/usr/sbin/grub-install -> ../lib/grub/i386-pc/grub-install[/COLOR]
[COLOR=#BB4444]chroot: failed to run command `grub-install'[/COLOR]: Input/output error
grub-install /dev/sda: [COLOR=#AA22FF]exit [/COLOR]code of grub-install /dev/sda:126

---- Grub-install verbose
chroot: failed to run [COLOR=#AA22FF]command[/COLOR] [COLOR=#BB4444]`[/COLOR]sh[COLOR=#BB4444]': Input/output error[/COLOR]
[COLOR=#BB4444]--------[/COLOR]
[COLOR=#BB4444]/usr/sbin/grub-install /dev/sda: exit code of grub-install /dev/sda:126[/COLOR]
[COLOR=#BB4444]---- End of grub-install verbose[/COLOR]


[COLOR=#BB4444]chroot /mnt/boot-sav/sda1 update-grub[/COLOR]
[COLOR=#BB4444]chroot: failed to run command `update-grub'[/COLOR]: Input/output error
Unhide GRUB boot menu in sda1/boot/grub/grub.cfg

Une erreur est survenue pendant la réparation.

Vous pouvez maintenant redémarrer votre ordinateur.
N[COLOR=#BB4444]'oubliez pas de régler votre BIOS pour qu'[/COLOR]il amorce sur le disque sda [COLOR=#666666]([/COLOR]500GB[COLOR=#666666])[/COLOR] !
pastebinit  packages needed
E: Le paquet « pastebinit » n[COLOR=#BB4444]'a pas de version susceptible d'[/COLOR]être installée
dpkg-preconfigure: impossible de réouvrir stdin : Aucun fichier ou dossier de ce [COLOR=#AA22FF]type[/COLOR][/COLOR]
[/TD]
[/TR]
[/TABLE]

```

May someone help me ?

Thanks in advance !

---

### Post by Sef on 2014-04-12
Try reinstalling [grub]("http://www.supergrubdisk.org/").

---

### Post by mths2 on 2014-04-12
I think grub has already been reinstalled by boot-repair, it has even been the first thing done by it. I'll try as soon as I can and post the results.

---

### Post by grahammechanical on 2014-04-12
> [COLOR=#BB4444][FONT=Ubuntu Mono]Reinstall the GRUB of sda1 into the MBR of sda[/FONT][/COLOR][COLOR=#BB4444][FONT=Ubuntu Mono]chroot: failed to run command `grub-install'[/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu Mono]: Input/output errorgrub-install /dev/sda: [/FONT][/COLOR][COLOR=#AA22FF][FONT=Ubuntu Mono]exit [/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu Mono]code of grub-install /dev/sda:126Failed to run [/FONT][/COLOR][COLOR=#AA22FF][FONT=Ubuntu Mono]command [/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu Mono]grub-install detected.[/FONT][/COLOR]

That says the attempt by BootRepair to install/reinstall Grub failed. And this says the attempt to update the Grub configuration files failed.

> [COLOR=#BB4444][FONT=Ubuntu Mono]chroot /mnt/boot-sav/sda1 update-grub[/FONT][/COLOR][COLOR=#BB4444][FONT=Ubuntu Mono]chroot: failed to run command `update-grub'[/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu Mono]: Input/output error[/FONT][/COLOR]

Why? what does this say?
> 
[COLOR=#000000][FONT=Ubuntu Mono]Une erreur est survenue pendant la réparation.Vous pouvez maintenant redémarrer votre ordinateur.N[/FONT][/COLOR][COLOR=#BB4444][FONT=Ubuntu Mono]'oubliez pas de régler votre BIOS pour qu'[/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu Mono]il amorce sur le disque sda [/FONT][/COLOR][COLOR=#666666][FONT=Ubuntu Mono]([/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu Mono]500GB[/FONT][/COLOR][COLOR=#666666][FONT=Ubuntu Mono])[/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu Mono] ![/FONT][/COLOR]

Have you considered, that as the system was up and running when it froze then the problem was nothing to do with Grub as Grub had already done it job and exited as the loading of the Linux kernel took over.

You need to give us the symptoms of what you mean by "impossible to boot." Describe what happens. Please consider a re-install of Ubuntu as an easy fix.

Regards.

---

### Post by oldfred on 2014-04-12
In addition, did you just do an upgrade?
You show many old 2.6 & 3.2 kernels and only one 3.5 kernel.
You should consider housecleaning old kernels once you get it going again.

I also have nVidia 9600GT and have to use nomodeset until I install the nVidia drivers.

Do not force shutdown if at all possible - remember the elephants. :)

       Never force shutdown your laptop. Use Alt+SysRq R-E-I-S-U-B instead. (For newer laptops they don't bother adding the SysRq print to the key, but it's the same as the PrtScr key)

   Holding down Alt and SysRq (which is the Print Screen key) while slowly typing REISUB
R-E-I-S-U-B to force shutdown
A good way to remember it is.
Raising Skinny Elephants Is Utterly Boring ...or
Reboot System Even If Ultimately Broken ...LOL.
[http://kember.net/articles/reisub-the-gentle-linux-restart/](http://kember.net/articles/reisub-the-gentle-linux-restart/)
[http://ubuntuforums.org/showthread.php?t=1509765&p=12543274#post12543274](http://ubuntuforums.org/showthread.php?t=1509765&p=12543274#post12543274)
[http://en.wikipedia.org/wiki/Magic_SysRq_key](http://en.wikipedia.org/wiki/Magic_SysRq_key)

---

