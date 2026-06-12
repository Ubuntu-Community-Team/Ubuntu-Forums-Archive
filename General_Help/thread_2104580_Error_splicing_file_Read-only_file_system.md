---
title: "Error splicing file: Read-only file system"
date: 2013-01-13
forum: General Help
---

### Post by sdowney717 on 2013-01-13
SO, I was copying files onto a NEW 1tb Toshiba hard drive and suddenly get error

> Error splicing file: Read-only file system

And the drive has vanished from Nautilus?
And gparted no longer sees sda drive?

I was copy 30gb in 3 separate files when this happened


dmesg shows tons of errors

```
[183065.875614] Buffer I/O error on device sda2, logical block 104612573
[183065.875616] Buffer I/O error on device sda2, logical block 104612574
[183065.875618] Buffer I/O error on device sda2, logical block 104612575
[183065.875620] Buffer I/O error on device sda2, logical block 104612576
[183065.875622] Buffer I/O error on device sda2, logical block 104612577
[183065.875623] Buffer I/O error on device sda2, logical block 104612578
[183065.875625] Buffer I/O error on device sda2, logical block 104612579
[183065.875627] Buffer I/O error on device sda2, logical block 104612580
[183065.875629] Buffer I/O error on device sda2, logical block 104612581
[183065.875631] Buffer I/O error on device sda2, logical block 104612582
[183065.875633] Buffer I/O error on device sda2, logical block 104612583
[183065.875634] Buffer I/O error on device sda2, logical block 104612584
[183065.875636] Buffer I/O error on device sda2, logical block 104612585
[183065.875638] Buffer I/O error on device sda2, logical block 104612586
[183065.875640] Buffer I/O error on device sda2, logical block 104612587
[183065.875642] Buffer I/O error on device sda2, logical block 104612588
[183065.875644] Buffer I/O error on device sda2, logical block 104612589
[183065.875646] Buffer I/O error on device sda2, logical block 104612590
[183065.875647] Buffer I/O error on device sda2, logical block 104612591
[183065.875649] Buffer I/O error on device sda2, logical block 104612592
[183065.875651] Buffer I/O error on device sda2, logical block 104612593
[183065.875653] Buffer I/O error on device sda2, logical block 104612594
[183065.875655] Buffer I/O error on device sda2, logical block 104612595
[183065.875657] Buffer I/O error on device sda2, logical block 104612596
[183065.875658] Buffer I/O error on device sda2, logical block 104612597
[183065.875660] Buffer I/O error on device sda2, logical block 104612598
[183065.875662] Buffer I/O error on device sda2, logical block 104612599
[183065.875664] Buffer I/O error on device sda2, logical block 104612600
[183065.875666] Buffer I/O error on device sda2, logical block 104612601
[183065.875668] Buffer I/O error on device sda2, logical block 104612602
[183065.875669] Buffer I/O error on device sda2, logical block 104612603
[183065.875671] Buffer I/O error on device sda2, logical block 104612604
[183065.875673] Buffer I/O error on device sda2, logical block 104612605
[183065.875675] Buffer I/O error on device sda2, logical block 104612606
[183065.875677] Buffer I/O error on device sda2, logical block 104612607
[183065.875680] EXT4-fs warning (device sda2): ext4_end_bio:250: I/O error writing to inode 14971431 (offset 4926734336 size 524288 starting block 226708616)
[183065.875682] Buffer I/O error on device sda2, logical block 104612608
[183065.875684] Buffer I/O error on device sda2, logical block 104612609
[183065.875686] Buffer I/O error on device sda2, logical block 104612610
[183065.875688] Buffer I/O error on device sda2, logical block 104612611
[183065.875690] Buffer I/O error on device sda2, logical block 104612612
[183065.875692] Buffer I/O error on device sda2, logical block 104612613
[183065.875693] Buffer I/O error on device sda2, logical block 104612614
[183065.875695] Buffer I/O error on device sda2, logical block 104612615
[183065.875697] Buffer I/O error on device sda2, logical block 104612616
[183065.875699] Buffer I/O error on device sda2, logical block 104612617
[183065.875701] Buffer I/O error on device sda2, logical block 104612618
[183065.875703] Buffer I/O error on device sda2, logical block 104612619
[183065.875704] Buffer I/O error on device sda2, logical block 104612620
[183065.875706] Buffer I/O error on device sda2, logical block 104612621
[183065.875708] Buffer I/O error on device sda2, logical block 104612622
[183065.875710] Buffer I/O error on device sda2, logical block 104612623
[183065.875712] Buffer I/O error on device sda2, logical block 104612624
[183065.875714] Buffer I/O error on device sda2, logical block 104612625
[183065.875716] Buffer I/O error on device sda2, logical block 104612626
[183065.875718] Buffer I/O error on device sda2, logical block 104612627
[183065.875719] Buffer I/O error on device sda2, logical block 104612628
[183065.875721] Buffer I/O error on device sda2, logical block 104612629
[183065.875723] Buffer I/O error on device sda2, logical block 104612630
[183065.875725] Buffer I/O error on device sda2, logical block 104612631
[183065.875727] Buffer I/O error on device sda2, logical block 104612632
[183065.875728] Buffer I/O error on device sda2, logical block 104612633
[183065.875730] Buffer I/O error on device sda2, logical block 104612634
[183065.875732] Buffer I/O error on device sda2, logical block 104612635
[183065.875734] Buffer I/O error on device sda2, logical block 104612636
[183065.875736] Buffer I/O error on device sda2, logical block 104612637
[183065.875738] Buffer I/O error on device sda2, logical block 104612638
[183065.875740] Buffer I/O error on device sda2, logical block 104612639
[183065.875741] Buffer I/O error on device sda2, logical block 104612640
[183065.875743] Buffer I/O error on device sda2, logical block 104612641
[183065.875745] Buffer I/O error on device sda2, logical block 104612642
[183065.875747] Buffer I/O error on device sda2, logical block 104612643
[183065.875749] Buffer I/O error on device sda2, logical block 104612644
[183065.875751] Buffer I/O error on device sda2, logical block 104612645
[183065.875752] Buffer I/O error on device sda2, logical block 104612646
[183065.875754] Buffer I/O error on device sda2, logical block 104612647
[183065.875756] Buffer I/O error on device sda2, logical block 104612648
[183065.875758] Buffer I/O error on device sda2, logical block 104612649
[183065.875760] Buffer I/O error on device sda2, logical block 104612650
[183065.875762] Buffer I/O error on device sda2, logical block 104612651
[183065.875763] Buffer I/O error on device sda2, logical block 104612652
[183065.875765] Buffer I/O error on device sda2, logical block 104612653
[183065.875767] Buffer I/O error on device sda2, logical block 104612654
[183065.875769] Buffer I/O error on device sda2, logical block 104612655
[183065.875771] Buffer I/O error on device sda2, logical block 104612656
[183065.875773] Buffer I/O error on device sda2, logical block 104612657
[183065.875775] Buffer I/O error on device sda2, logical block 104612658
[183065.875776] Buffer I/O error on device sda2, logical block 104612659
[183065.875778] Buffer I/O error on device sda2, logical block 104612660
[183065.875780] Buffer I/O error on device sda2, logical block 104612661
[183065.875782] Buffer I/O error on device sda2, logical block 104612662
[183065.875784] Buffer I/O error on device sda2, logical block 104612663
[183065.875786] Buffer I/O error on device sda2, logical block 104612664
[183065.875787] Buffer I/O error on device sda2, logical block 104612665
[183065.875789] Buffer I/O error on device sda2, logical block 104612666
[183065.875791] Buffer I/O error on device sda2, logical block 104612667
[183065.875793] Buffer I/O error on device sda2, logical block 104612668
[183065.875795] Buffer I/O error on device sda2, logical block 104612669
[183065.875797] Buffer I/O error on device sda2, logical block 104612670
[183065.875799] Buffer I/O error on device sda2, logical block 104612671
[183065.875800] Buffer I/O error on device sda2, logical block 104612672
[183065.875802] Buffer I/O error on device sda2, logical block 104612673
[183065.875804] Buffer I/O error on device sda2, logical block 104612674
[183065.875806] Buffer I/O error on device sda2, logical block 104612675
[183065.875808] Buffer I/O error on device sda2, logical block 104612676
[183065.875810] Buffer I/O error on device sda2, logical block 104612677
[183065.875812] Buffer I/O error on device sda2, logical block 104612678
[183065.875814] Buffer I/O error on device sda2, logical block 104612679
[183065.875815] Buffer I/O error on device sda2, logical block 104612680
[183065.875817] Buffer I/O error on device sda2, logical block 104612681
[183065.875819] Buffer I/O error on device sda2, logical block 104612682
[183065.875821] Buffer I/O error on device sda2, logical block 104612683
[183065.875823] Buffer I/O error on device sda2, logical block 104612684
[183065.875825] Buffer I/O error on device sda2, logical block 104612685
[183065.875826] Buffer I/O error on device sda2, logical block 104612686
[183065.875828] Buffer I/O error on device sda2, logical block 104612687
[183065.875830] Buffer I/O error on device sda2, logical block 104612688
[183065.875832] Buffer I/O error on device sda2, logical block 104612689
[183065.875834] Buffer I/O error on device sda2, logical block 104612690
[183065.875836] Buffer I/O error on device sda2, logical block 104612691
[183065.875837] Buffer I/O error on device sda2, logical block 104612692
[183065.875839] Buffer I/O error on device sda2, logical block 104612693
[183065.875841] Buffer I/O error on device sda2, logical block 104612694
[183065.875843] Buffer I/O error on device sda2, logical block 104612695
[183065.875845] Buffer I/O error on device sda2, logical block 104612696
[183065.875847] Buffer I/O error on device sda2, logical block 104612697
[183065.875849] Buffer I/O error on device sda2, logical block 104612698
[183065.875850] Buffer I/O error on device sda2, logical block 104612699
[183065.875852] Buffer I/O error on device sda2, logical block 104612700
[183065.875854] Buffer I/O error on device sda2, logical block 104612701
[183065.875856] Buffer I/O error on device sda2, logical block 104612702
[183065.875858] Buffer I/O error on device sda2, logical block 104612703
[183065.875860] Buffer I/O error on device sda2, logical block 104612704
[183065.875862] Buffer I/O error on device sda2, logical block 104612705
[183065.875863] Buffer I/O error on device sda2, logical block 104612706
[183065.875865] Buffer I/O error on device sda2, logical block 104612707
[183065.875867] Buffer I/O error on device sda2, logical block 104612708
[183065.875869] Buffer I/O error on device sda2, logical block 104612709
[183065.875871] Buffer I/O error on device sda2, logical block 104612710
[183065.875873] Buffer I/O error on device sda2, logical block 104612711
[183065.875874] Buffer I/O error on device sda2, logical block 104612712
[183065.875876] Buffer I/O error on device sda2, logical block 104612713
[183065.875878] Buffer I/O error on device sda2, logical block 104612714
[183065.875880] Buffer I/O error on device sda2, logical block 104612715
[183065.875882] Buffer I/O error on device sda2, logical block 104612716
[183065.875883] Buffer I/O error on device sda2, logical block 104612717
[183065.875885] Buffer I/O error on device sda2, logical block 104612718
[183065.875887] Buffer I/O error on device sda2, logical block 104612719
[183065.875889] Buffer I/O error on device sda2, logical block 104612720
[183065.875891] Buffer I/O error on device sda2, logical block 104612721
[183065.875893] Buffer I/O error on device sda2, logical block 104612722
[183065.875895] Buffer I/O error on device sda2, logical block 104612723
[183065.875896] Buffer I/O error on device sda2, logical block 104612724
[183065.875898] Buffer I/O error on device sda2, logical block 104612725
[183065.875900] Buffer I/O error on device sda2, logical block 104612726
[183065.875902] Buffer I/O error on device sda2, logical block 104612727
[183065.875904] Buffer I/O error on device sda2, logical block 104612728
[183065.875906] Buffer I/O error on device sda2, logical block 104612729
[183065.875907] Buffer I/O error on device sda2, logical block 104612730
[183065.875909] Buffer I/O error on device sda2, logical block 104612731
[183065.875911] Buffer I/O error on device sda2, logical block 104612732
[183065.875913] Buffer I/O error on device sda2, logical block 104612733
[183065.875915] Buffer I/O error on device sda2, logical block 104612734
[183065.875916] Buffer I/O error on device sda2, logical block 104612735
[183065.875919] EXT4-fs warning (device sda2): ext4_end_bio:250: I/O error writing to inode 14971431 (offset 4927258624 size 524288 starting block 226708744)
[183065.875922] Buffer I/O error on device sda2, logical block 104612736
[183065.875924] Buffer I/O error on device sda2, logical block 104612737
[183065.875926] Buffer I/O error on device sda2, logical block 104612738
[183065.875928] Buffer I/O error on device sda2, logical block 104612739
[183065.875929] Buffer I/O error on device sda2, logical block 104612740
[183065.875931] Buffer I/O error on device sda2, logical block 104612741
[183065.875933] Buffer I/O error on device sda2, logical block 104612742
[183065.875935] Buffer I/O error on device sda2, logical block 104612743
[183065.875937] Buffer I/O error on device sda2, logical block 104612744
[183065.875938] Buffer I/O error on device sda2, logical block 104612745
[183065.875940] Buffer I/O error on device sda2, logical block 104612746
[183065.875942] Buffer I/O error on device sda2, logical block 104612747
[183065.875944] Buffer I/O error on device sda2, logical block 104612748
[183065.875946] Buffer I/O error on device sda2, logical block 104612749
[183065.875947] Buffer I/O error on device sda2, logical block 104612750
[183065.875949] Buffer I/O error on device sda2, logical block 104612751
[183065.875951] Buffer I/O error on device sda2, logical block 104612752
[183065.875953] Buffer I/O error on device sda2, logical block 104612753
[183065.875954] Buffer I/O error on device sda2, logical block 104612754
[183065.875956] Buffer I/O error on device sda2, logical block 104612755
[183065.875958] Buffer I/O error on device sda2, logical block 104612756
[183065.875960] Buffer I/O error on device sda2, logical block 104612757
[183065.875962] Buffer I/O error on device sda2, logical block 104612758
[183065.875964] Buffer I/O error on device sda2, logical block 104612759
[183065.875965] Buffer I/O error on device sda2, logical block 104612760
[183065.875967] Buffer I/O error on device sda2, logical block 104612761
[183065.875969] Buffer I/O error on device sda2, logical block 104612762
[183065.875971] Buffer I/O error on device sda2, logical block 104612763
[183065.875972] Buffer I/O error on device sda2, logical block 104612764
[183065.875974] Buffer I/O error on device sda2, logical block 104612765
[183065.875976] Buffer I/O error on device sda2, logical block 104612766
[183065.875978] Buffer I/O error on device sda2, logical block 104612767
[183065.875980] Buffer I/O error on device sda2, logical block 104612768
[183065.875982] Buffer I/O error on device sda2, logical block 104612769
[183065.875983] Buffer I/O error on device sda2, logical block 104612770
[183065.875985] Buffer I/O error on device sda2, logical block 104612771
[183065.875987] Buffer I/O error on device sda2, logical block 104612772
[183065.875989] Buffer I/O error on device sda2, logical block 104612773
[183065.875991] Buffer I/O error on device sda2, logical block 104612774
[183065.875992] Buffer I/O error on device sda2, logical block 104612775
[183065.875994] Buffer I/O error on device sda2, logical block 104612776
[183065.875996] Buffer I/O error on device sda2, logical block 104612777
[183065.875998] Buffer I/O error on device sda2, logical block 104612778
[183065.876000] Buffer I/O error on device sda2, logical block 104612779
[183065.876001] Buffer I/O error on device sda2, logical block 104612780
[183065.876003] Buffer I/O error on device sda2, logical block 104612781
[183065.876005] Buffer I/O error on device sda2, logical block 104612782
[183065.876007] Buffer I/O error on device sda2, logical block 104612783
[183065.876009] Buffer I/O error on device sda2, logical block 104612784
[183065.876010] Buffer I/O error on device sda2, logical block 104612785
[183065.876012] Buffer I/O error on device sda2, logical block 104612786
[183065.876014] Buffer I/O error on device sda2, logical block 104612787
[183065.876016] Buffer I/O error on device sda2, logical block 104612788
[183065.876017] Buffer I/O error on device sda2, logical block 104612789
[183065.876019] Buffer I/O error on device sda2, logical block 104612790
[183065.876021] Buffer I/O error on device sda2, logical block 104612791
[183065.876023] Buffer I/O error on device sda2, logical block 104612792
[183065.876025] Buffer I/O error on device sda2, logical block 104612793
[183065.876026] Buffer I/O error on device sda2, logical block 104612794
[183065.876028] Buffer I/O error on device sda2, logical block 104612795
[183065.876030] Buffer I/O error on device sda2, logical block 104612796
[183065.876032] Buffer I/O error on device sda2, logical block 104612797
[183065.876033] Buffer I/O error on device sda2, logical block 104612798
[183065.876035] Buffer I/O error on device sda2, logical block 104612799
[183065.876037] Buffer I/O error on device sda2, logical block 104612800
[183065.876039] Buffer I/O error on device sda2, logical block 104612801
[183065.876041] Buffer I/O error on device sda2, logical block 104612802
[183065.876042] Buffer I/O error on device sda2, logical block 104612803
[183065.876044] Buffer I/O error on device sda2, logical block 104612804
[183065.876046] Buffer I/O error on device sda2, logical block 104612805
[183065.876048] Buffer I/O error on device sda2, logical block 104612806
[183065.876049] Buffer I/O error on device sda2, logical block 104612807
[183065.876051] Buffer I/O error on device sda2, logical block 104612808
[183065.876053] Buffer I/O error on device sda2, logical block 104612809
[183065.876055] Buffer I/O error on device sda2, logical block 104612810
[183065.876056] Buffer I/O error on device sda2, logical block 104612811
[183065.876058] Buffer I/O error on device sda2, logical block 104612812
[183065.876060] Buffer I/O error on device sda2, logical block 104612813
[183065.876062] Buffer I/O error on device sda2, logical block 104612814
[183065.876064] Buffer I/O error on device sda2, logical block 104612815
[183065.876066] Buffer I/O error on device sda2, logical block 104612816
[183065.876067] Buffer I/O error on device sda2, logical block 104612817
[183065.876069] Buffer I/O error on device sda2, logical block 104612818
[183065.876071] Buffer I/O error on device sda2, logical block 104612819
[183065.876073] Buffer I/O error on device sda2, logical block 104612820
[183065.876074] Buffer I/O error on device sda2, logical block 104612821
[183065.876076] Buffer I/O error on device sda2, logical block 104612822
[183065.876078] Buffer I/O error on device sda2, logical block 104612823
[183065.876080] Buffer I/O error on device sda2, logical block 104612824
[183065.876082] Buffer I/O error on device sda2, logical block 104612825
[183065.876083] Buffer I/O error on device sda2, logical block 104612826
[183065.876085] Buffer I/O error on device sda2, logical block 104612827
[183065.876087] Buffer I/O error on device sda2, logical block 104612828
[183065.876089] Buffer I/O error on device sda2, logical block 104612829
[183065.876090] Buffer I/O error on device sda2, logical block 104612830
[183065.876092] Buffer I/O error on device sda2, logical block 104612831
[183065.876094] Buffer I/O error on device sda2, logical block 104612832
[183065.876096] Buffer I/O error on device sda2, logical block 104612833
[183065.876097] Buffer I/O error on device sda2, logical block 104612834
[183065.876099] Buffer I/O error on device sda2, logical block 104612835
[183065.876101] Buffer I/O error on device sda2, logical block 104612836
[183065.876103] Buffer I/O error on device sda2, logical block 104612837
[183065.876105] Buffer I/O error on device sda2, logical block 104612838
[183065.876106] Buffer I/O error on device sda2, logical block 104612839
[183065.876108] Buffer I/O error on device sda2, logical block 104612840
[183065.876110] Buffer I/O error on device sda2, logical block 104612841
[183065.876112] Buffer I/O error on device sda2, logical block 104612842
[183065.876113] Buffer I/O error on device sda2, logical block 104612843
[183065.876115] Buffer I/O error on device sda2, logical block 104612844
[183065.876117] Buffer I/O error on device sda2, logical block 104612845
[183065.876119] Buffer I/O error on device sda2, logical block 104612846
[183065.876121] Buffer I/O error on device sda2, logical block 104612847
[183065.876122] Buffer I/O error on device sda2, logical block 104612848
[183065.876124] Buffer I/O error on device sda2, logical block 104612849
[183065.876126] Buffer I/O error on device sda2, logical block 104612850
[183065.876128] Buffer I/O error on device sda2, logical block 104612851
[183065.876129] Buffer I/O error on device sda2, logical block 104612852
[183065.876131] Buffer I/O error on device sda2, logical block 104612853
[183065.876133] Buffer I/O error on device sda2, logical block 104612854
[183065.876135] Buffer I/O error on device sda2, logical block 104612855
[183065.876136] Buffer I/O error on device sda2, logical block 104612856
[183065.876138] Buffer I/O error on device sda2, logical block 104612857
[183065.876140] Buffer I/O error on device sda2, logical block 104612858
[183065.876142] Buffer I/O error on device sda2, logical block 104612859
[183065.876143] Buffer I/O error on device sda2, logical block 104612860
[183065.876145] Buffer I/O error on device sda2, logical block 104612861
[183065.876147] Buffer I/O error on device sda2, logical block 104612862
[183065.876149] Buffer I/O error on device sda2, logical block 104612863
[183065.876152] EXT4-fs warning (device sda2): ext4_end_bio:250: I/O error writing to inode 14971431 (offset 4927782912 size 524288 starting block 226708872)
[183065.876154] Buffer I/O error on device sda2, logical block 104612864
[183065.876156] Buffer I/O error on device sda2, logical block 104612865
[183065.876158] Buffer I/O error on device sda2, logical block 104612866
[183065.876160] Buffer I/O error on device sda2, logical block 104612867
[183065.876162] Buffer I/O error on device sda2, logical block 104612868
[183065.876164] Buffer I/O error on device sda2, logical block 104612869
[183065.876165] Buffer I/O error on device sda2, logical block 104612870
[183065.876167] Buffer I/O error on device sda2, logical block 104612871
[183065.876169] Buffer I/O error on device sda2, logical block 104612872
[183065.876171] Buffer I/O error on device sda2, logical block 104612873
[183065.876172] Buffer I/O error on device sda2, logical block 104612874
[183065.876174] Buffer I/O error on device sda2, logical block 104612875
[183065.876176] Buffer I/O error on device sda2, logical block 104612876
[183065.876178] Buffer I/O error on device sda2, logical block 104612877
[183065.876180] Buffer I/O error on device sda2, logical block 104612878
[183065.876181] Buffer I/O error on device sda2, logical block 104612879
[183065.876183] Buffer I/O error on device sda2, logical block 104612880
[183065.876185] Buffer I/O error on device sda2, logical block 104612881
[183065.876187] Buffer I/O error on device sda2, logical block 104612882
[183065.876188] Buffer I/O error on device sda2, logical block 104612883
[183065.876190] Buffer I/O error on device sda2, logical block 104612884
[183065.876192] Buffer I/O error on device sda2, logical block 104612885
[183065.876194] Buffer I/O error on device sda2, logical block 104612886
[183065.876195] Buffer I/O error on device sda2, logical block 104612887
[183065.876197] Buffer I/O error on device sda2, logical block 104612888
[183065.876199] Buffer I/O error on device sda2, logical block 104612889
[183065.876201] Buffer I/O error on device sda2, logical block 104612890
[183065.876202] Buffer I/O error on device sda2, logical block 104612891
[183065.876204] Buffer I/O error on device sda2, logical block 104612892
[183065.876206] Buffer I/O error on device sda2, logical block 104612893
[183065.876208] Buffer I/O error on device sda2, logical block 104612894
[183065.876209] Buffer I/O error on device sda2, logical block 104612895
[183065.876211] Buffer I/O error on device sda2, logical block 104612896
[183065.876213] Buffer I/O error on device sda2, logical block 104612897
[183065.876215] Buffer I/O error on device sda2, logical block 104612898
[183065.876217] Buffer I/O error on device sda2, logical block 104612899
[183065.876218] Buffer I/O error on device sda2, logical block 104612900
[183065.876220] Buffer I/O error on device sda2, logical block 104612901
[183065.876222] Buffer I/O error on device sda2, logical block 104612902
[183065.876224] Buffer I/O error on device sda2, logical block 104612903
[183065.876225] Buffer I/O error on device sda2, logical block 104612904
[183065.876227] Buffer I/O error on device sda2, logical block 104612905
[183065.876229] Buffer I/O error on device sda2, logical block 104612906
[183065.876231] Buffer I/O error on device sda2, logical block 104612907
[183065.876233] Buffer I/O error on device sda2, logical block 104612908
[183065.876234] Buffer I/O error on device sda2, logical block 104612909
[183065.876236] Buffer I/O error on device sda2, logical block 104612910
[183065.876238] Buffer I/O error on device sda2, logical block 104612911
[183065.876240] Buffer I/O error on device sda2, logical block 104612912
[183065.876242] Buffer I/O error on device sda2, logical block 104612913
[183065.876243] Buffer I/O error on device sda2, logical block 104612914
[183065.876245] Buffer I/O error on device sda2, logical block 104612915
[183065.876247] Buffer I/O error on device sda2, logical block 104612916
[183065.876249] Buffer I/O error on device sda2, logical block 104612917
[183065.876250] Buffer I/O error on device sda2, logical block 104612918
[183065.876252] Buffer I/O error on device sda2, logical block 104612919
[183065.876254] Buffer I/O error on device sda2, logical block 104612920
[183065.876256] Buffer I/O error on device sda2, logical block 104612921
[183065.876257] Buffer I/O error on device sda2, logical block 104612922
[183065.876259] Buffer I/O error on device sda2, logical block 104612923
[183065.876261] Buffer I/O error on device sda2, logical block 104612924
[183065.876263] Buffer I/O error on device sda2, logical block 104612925
[183065.876265] Buffer I/O error on device sda2, logical block 104612926
[183065.876266] Buffer I/O error on device sda2, logical block 104612927
[183065.876268] Buffer I/O error on device sda2, logical block 104612928
[183065.876270] Buffer I/O error on device sda2, logical block 104612929
[183065.876272] Buffer I/O error on device sda2, logical block 104612930
[183065.876274] Buffer I/O error on device sda2, logical block 104612931
[183065.876275] Buffer I/O error on device sda2, logical block 104612932
[183065.876277] Buffer I/O error on device sda2, logical block 104612933
[183065.876279] Buffer I/O error on device sda2, logical block 104612934
[183065.876281] Buffer I/O error on device sda2, logical block 104612935
[183065.876283] Buffer I/O error on device sda2, logical block 104612936
[183065.876284] Buffer I/O error on device sda2, logical block 104612937
[183065.876286] Buffer I/O error on device sda2, logical block 104612938
[183065.876288] Buffer I/O error on device sda2, logical block 104612939
[183065.876290] Buffer I/O error on device sda2, logical block 104612940
[183065.876291] Buffer I/O error on device sda2, logical block 104612941
[183065.876293] Buffer I/O error on device sda2, logical block 104612942
[183065.876295] Buffer I/O error on device sda2, logical block 104612943
[183065.876298] EXT4-fs warning (device sda2): ext4_end_bio:250: I/O error writing to inode 14971431 (offset 4928307200 size 327680 starting block 226708952)
[183065.876320] JBD2: Detected IO errors while flushing file data on sda2-8
[183065.876335] Aborting journal on device sda2-8.
[183065.876341] JBD2: Error -5 detected when updating journal superblock for sda2-8.
[183065.884604] EXT4-fs error (device sda2): ext4_journal_start_sb:370: Detected aborted journal
[183065.884610] EXT4-fs (sda2): Remounting filesystem read-only
[183065.884613] EXT4-fs (sda2): previous I/O error to superblock detected
[183065.884620] EXT4-fs (sda2): ext4_da_writepages: jbd2_start: 9223372036854775807 pages, ino 14971432; err -30
[183065.897805] JBD2: Detected IO errors while flushing file data on sda2-8
[183065.897821] journal commit I/O error
[183065.900128] sd 1:0:1:0: [sda] Synchronizing SCSI cache
[183065.900155] sd 1:0:1:0: [sda]  
[183065.900158] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
[183065.900160] sd 1:0:1:0: [sda] Stopping disk
[183065.900168] sd 1:0:1:0: [sda] START_STOP FAILED
[183065.900170] sd 1:0:1:0: [sda]  
[183065.900171] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
[183065.946072] EXT4-fs error (device sda2): ext4_find_entry:1209: inode #2: comm pool: reading directory lblock 0
[183065.946132] EXT4-fs error (device sda2): ext4_find_entry:1209: inode #2: comm pool: reading directory lblock 0
[183066.024509] EXT4-fs error (device sda2): ext4_wait_block_bitmap:447: comm queue61:src: Cannot read block bitmap - block_group = 3192, block_bitmap = 104333320
[183066.024516] EXT4-fs error (device sda2): ext4_discard_preallocations:3838: comm queue61:src: Error reading block bitmap for 3192
[183601.429803] type=1701 audit(1358107625.470:4604): auid=4294967295 uid=1000 gid=1000 ses=4294967295 pid=18512 comm="chrome" reason="seccomp" sig=0 syscall=257 compat=0 ip=0x7fa874734710 code=0x50000
[183601.429812] type=1701 audit(1358107625.470:4605): auid=4294967295 uid=1000 gid=1000 ses=4294967295 pid=18512 comm="chrome" reason="seccomp" sig=0 syscall=2 compat=0 ip=0x7fa8747346b0 code=0x50000
[183601.429818] type=1701 audit(1358107625.470:4606): auid=4294967295 uid=1000 gid=1000 ses=4294967295 pid=18512 comm="chrome" reason="seccomp" sig=0 syscall=2 compat=0 ip=0x7fa8747346b0 code=0x50000
[183601.429824] type=1701 audit(1358107625.470:4607): auid=4294967295 uid=1000 gid=1000 ses=4294967295 pid=18512 comm="chrome" reason="seccomp" sig=0 syscall=2 compat=0 ip=0x7fa8747346b0 code=0x50000
[183602.403223] type=1701 audit(1358107626.442:4608): auid=4294967295 uid=1000 gid=1000 ses=4294967295 pid=18512 comm="chrome" reason="seccomp" sig=0 syscall=257 compat=0 ip=0x7fa874734710 code=0x50000
[183602.403232] type=1701 audit(1358107626.442:4609): auid=4294967295 uid=1000 gid=1000 ses=4294967295 pid=18512 comm="chrome" reason="seccomp" sig=0 syscall=2 compat=0 ip=0x7fa8747346b0 code=0x50000
[183602.403238] type=1701 audit(1358107626.442:4610): auid=4294967295 uid=1000 gid=1000 ses=4294967295 pid=18512 comm="chrome" reason="seccomp" sig=0 syscall=2 compat=0 ip=0x7fa8747346b0 code=0x50000
[183602.403244] type=1701 audit(1358107626.442:4611): auid=4294967295 uid=1000 gid=1000 ses=4294967295 pid=18512 comm="chrome" reason="seccomp" sig=0 syscall=2 compat=0 ip=0x7fa8747346b0 code=0x50000
[183675.618883] type=1701 audit(1358107699.658:4612): auid=4294967295 uid=1000 gid=1000 ses=4294967295 pid=18512 comm="chrome" reason="seccomp" sig=0 syscall=257 compat=0 ip=0x7fa874734710 code=0x50000
[183675.618893] type=1701 audit(1358107699.658:4613): auid=4294967295 uid=1000 gid=1000 ses=4294967295 pid=18512 comm="chrome" reason="seccomp" sig=0 syscall=2 compat=0 ip=0x7fa8747346b0 code=0x50000
[183675.618899] type=1701 audit(1358107699.658:4614): auid=4294967295 uid=1000 gid=1000 ses=4294967295 pid=18512 comm="chrome" reason="seccomp" sig=0 syscall=2 compat=0 ip=0x7fa8747346b0 code=0x50000
[183675.618905] type=1701 audit(1358107699.658:4615): auid=4294967295 uid=1000 gid=1000 ses=4294967295 pid=18512 comm="chrome" reason="seccomp" sig=0 syscall=2 compat=0 ip=0x7fa8747346b0 code=0x50000
[183720.603382] type=1701 audit(1358107744.642:4616): auid=4294967295 uid=1000 gid=1000 ses=4294967295 pid=18512 comm="chrome" reason="seccomp" sig=0 syscall=257 compat=0 ip=0x7fa874734710 code=0x50000
[183720.603392] type=1701 audit(1358107744.642:4617): auid=4294967295 uid=1000 gid=1000 ses=4294967295 pid=18512 comm="chrome" reason="seccomp" sig=0 syscall=2 compat=0 ip=0x7fa8747346b0 code=0x50000
[183720.603398] type=1701 audit(1358107744.642:4618): auid=4294967295 uid=1000 gid=1000 ses=4294967295 pid=18512 comm="chrome" reason="seccomp" sig=0 syscall=2 compat=0 ip=0x7fa8747346b0 code=0x50000
[183720.603404] type=1701 audit(1358107744.642:4619): auid=4294967295 uid=1000 gid=1000 ses=4294967295 pid=18512 comm="chrome" reason="seccomp" sig=0 syscall=2 compat=0 ip=0x7fa8747346b0 code=0x50000
[183720.950736] type=1701 audit(1358107744.990:4620): auid=4294967295 uid=1000 gid=1000 ses=4294967295 pid=18512 comm="chrome" reason="seccomp" sig=0 syscall=257 compat=0 ip=0x7fa874734710 code=0x50000
[183982.060876] type=1701 audit(1358108006.102:4621): auid=4294967295 uid=1000 gid=1000 ses=4294967295 pid=2046 comm="chrome" reason="seccomp" sig=0 syscall=4 compat=0 ip=0x7fa874734205 code=0x50000
[183982.060885] type=1701 audit(1358108006.102:4622): auid=4294967295 uid=1000 gid=1000 ses=4294967295 pid=2046 comm="chrome" reason="seccomp" sig=0 syscall=4 compat=0 ip=0x7fa874734205 code=0x50000
[183982.060890] type=1701 audit(1358108006.102:4623): auid=4294967295 uid=1000 gid=1000 ses=4294967295 pid=2046 comm="chrome" reason="seccomp" sig=0 syscall=4 compat=0 ip=0x7fa874734205 code=0x50000
[183982.060896] type=1701 audit(1358108006.102:4624): auid=4294967295 uid=1000 gid=1000 ses=4294967295 pid=2046 comm="chrome" reason="seccomp" sig=0 syscall=4 compat=0 ip=0x7fa874734205 code=0x50000
[183982.060902] type=1701 audit(1358108006.102:4625): auid=4294967295 uid=1000 gid=1000 ses=4294967295 pid=2046 comm="chrome" reason="seccomp" sig=0 syscall=4 compat=0 ip=0x7fa874734205 code=0x50000
[183983.075417] type=1701 audit(1358108007.114:4626): auid=4294967295 uid=1000 gid=1000 ses=4294967295 pid=2046 comm="chrome" reason="seccomp" sig=0 syscall=2 compat=0 ip=0x7fa8747346b0 code=0x50000
[183986.921200] type=1701 audit(1358108010.962:4627): auid=4294967295 uid=1000 gid=1000 ses=4294967295 pid=18512 comm="chrome" reason="seccomp" sig=0 syscall=257 compat=0 ip=0x7fa874734710 code=0x50000
[183986.921210] type=1701 audit(1358108010.962:4628): auid=4294967295 uid=1000 gid=1000 ses=4294967295 pid=18512 comm="chrome" reason="seccomp" sig=0 syscall=2 compat=0 ip=0x7fa8747346b0 code=0x50000
[183986.921216] type=1701 audit(1358108010.962:4629): auid=4294967295 uid=1000 gid=1000 ses=4294967295 pid=18512 comm="chrome" reason="seccomp" sig=0 syscall=2 compat=0 ip=0x7fa8747346b0 code=0x50000
[183986.921221] type=1701 audit(1358108010.962:4630): auid=4294967295 uid=1000 gid=1000 ses=4294967295 pid=18512 comm="chrome" reason="seccomp" sig=0 syscall=2 compat=0 ip=0x7fa8747346b0 code=0x50000
[184080.952705] audit_printk_skb: 12 callbacks suppressed
[184080.952709] type=1701 audit(1358108104.994:4635): auid=4294967295 uid=1000 gid=1000 ses=4294967295 pid=18512 comm="chrome" reason="seccomp" sig=0 syscall=257 compat=0 ip=0x7fa874734710 code=0x50000
[184080.952718] type=1701 audit(1358108104.994:4636): auid=4294967295 uid=1000 gid=1000 ses=4294967295 pid=18512 comm="chrome" reason="seccomp" sig=0 syscall=2 compat=0 ip=0x7fa8747346b0 code=0x50000
[184080.952724] type=1701 audit(1358108104.994:4637): auid=4294967295 uid=1000 gid=1000 ses=4294967295 pid=18512 comm="chrome" reason="seccomp" sig=0 syscall=2 compat=0 ip=0x7fa8747346b0 code=0x50000
[184080.952729] type=1701 audit(1358108104.994:4638): auid=4294967295 uid=1000 gid=1000 ses=4294967295 pid=18512 comm="chrome" reason="seccomp" sig=0 syscall=2 compat=0 ip=0x7fa8747346b0 code=0x50000
[184081.246019] type=1701 audit(1358108105.286:4639): auid=4294967295 uid=1000 gid=1000 ses=4294967295 pid=18512 comm="chrome" reason="seccomp" sig=0 syscall=257 compat=0 ip=0x7fa874734710 code=0x50000
[184081.246028] type=1701 audit(1358108105.286:4640): auid=4294967295 uid=1000 gid=1000 ses=4294967295 pid=18512 comm="chrome" reason="seccomp" sig=0 syscall=2 compat=0 ip=0x7fa8747346b0 code=0x50000
[184081.246034] type=1701 audit(1358108105.286:4641): auid=4294967295 uid=1000 gid=1000 ses=4294967295 pid=18512 comm="chrome" reason="seccomp" sig=0 syscall=2 compat=0 ip=0x7fa8747346b0 code=0x50000
[184081.246040] type=1701 audit(1358108105.286:4642): auid=4294967295 uid=1000 gid=1000 ses=4294967295 pid=18512 comm="chrome" reason="seccomp" sig=0 syscall=2 compat=0 ip=0x7fa8747346b0 code=0x50000
scott@scott-P5QC:~$ 

```

---

### Post by sdowney717 on 2013-01-13
Drive is no longer seen in the PC bios, so it has died. IMO
It spins up, but the bios does not report any drive there.
This is a 1tb toshiba sata3 DT01ACA100 drive.

I have heard you can put a drive in the freezer.
Anyone think the data cable went bad?

---

### Post by sdowney717 on 2013-01-13
replaced the Rosewill sata 3 data cable from new egg with a second rosewill sata 3 data cable from new egg and the hard drive is back.

So cable could be bad.
or the port motherboard or drive overheated.
I hope just the cable.

Doing another copy, this time 4 large files simultaneously to see if it can.

---

### Post by tgalati4 on 2013-01-13
Drives are electro-mechanical devices with many failure modes.  Your stress test will certainly ring out the drive.  Performing long writes can cause the heads to heat up and deform or delaminate--for instance music or video recording to hard disk.

I run badblocks on a drive before using it.  It helps to break the drive in gradually before putting it in service.

It's rare for a cable to go bad, but I/O chipsets heat up and can fail at both ends of the SATA chain.

---

### Post by sdowney717 on 2013-01-14
Drive and new cable are so far working ok. Drive has 3 year warranty.

---

