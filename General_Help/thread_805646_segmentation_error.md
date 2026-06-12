---
title: "segmentation error"
date: 2008-05-24
forum: General Help
---

### Post by dinesh2n on 2008-05-24
Hello friends!
 I am working on a scientific code. The older version of the code is running properly. But there is problem newer version. The data of INC_FLUID of newer version is also running; but INC_MHD newer version showing error though INC_FLUID and INC_MHD are similar in nature
In nwer version of INC_MHD; Terminal showed few data upto middle and stops by stating following "Segmentation" error and some "warning" lines are also there which was not in the INC_MHD(older version):

dinesh@localhost:~/data_file_new/SPECTRAL/trunk/src$ ./RUN
PROG_kind = INC_MHD
data_dir_name = /home/dinesh/data_file_new/data/fluid3d_8cube/input_MHD/ D
= 3
=========== Reading field parameters ===========

        N[i]: 8 8 8

        Diss_coefficient: 0.01 0.001

        Basis_type: FOUR

        Aliasing_switch: DEALIAS

        Integrating Scheme: EULER

        Low_dimension_switch (1 means yes, 0 means no): 0

        les_switch (1 means yes, 0 means no): 0

        time_para (t0, tfinal, dt): 0 0.1 0.01 0

        time_save: 0.01 0.01 1 1 1 1 1 1 0.001

        number output field mode (ASCII or BINARY): ASCII

        N_out_reduced[i]: 4 4 2

        Energy transfer nospheres, noshells, shell_input_scheme,
real_imag_switch: 8 8 0 0

No of field wavenumbers whose field values and Tk are to be printed: 6 kx,
ky, kz: 1 1 1
kx, ky, kz: 2 2 1
kx, ky, kz: 1 1 1
kx, ky, kz: 3 3 2
kx, ky, kz: 2 2 0
kx, ky, kz: 3 3 0
===========================================

=========== Reading Init condition parameters ===========

        Field_input_proc: 3

        N_in_reduced[i]: 8 8 8

        number input field mode (ASCII or BINARY): ASCII

        number of init cond para: 1

        Init condition parameter: 1

===========================================

=========== Reading force parameters ===========

        Force_field_proc: 0

        number of force para: 4

        Force field parameter: 2 3 0.1 0

===========================================

WARNING: NO OF ENERGY TR SHELLS SHOULD BE GREATER THAN EQUAL TO FIVE OR
Maxpossible inner radius should be greater that equal to 16
Dont invoke flux and shell-to-shell routines.
Maxrad and the radii of the sphere are 4
9
 [ 0 2 4 8 5.03968 3.1748 2
          4 10000 ]

Output_k_array(-, kx, ky, kz) 7 x 4
[ 0 0 0 0
          0 1 1 1
          0 2 2 1
          0 1 1 1
          0 3 3 2
          0 2 2 0
          0 3 3 0 ]

WARNING: NO OF ENERGY TR SHELLS SHOULD BE GREATER THAN EQUAL TO FIVE OR
Maxpossible inner radius should be greater that equal to 16
Dont invoke flux and shell-to-shell routines.
Maxrad and the radii of the sphere are 4
9
 [ 0 2 4 8 5.03968 3.1748 2
          4 10000 ]

Reading field configurations from field_in_file
=== Reading field wavenumbers and Vx ====
./RUN: line 6: 6255 Segmentation fault ./RB INC_MHD
/home/dinesh/data_file_new/data/fluid3d_8cube/input_MHD/ 3
dinesh@localhost:~/data_file_new/SPECTRAL/trunk/src$

and the programme did't run further. If I guess, the problem might bebecause of those warnings. So kindly, let me know where the problem has
occurred? I have read that segmentation error occurs by memory overwrites or non allowed memory region touch.....
but what could be the reason here....
I have deleted th all new version files and again reset still same problem is went on....how to remove this segmentation error ..will I have to remove some files ..if Yes what will be those?
Kindly help me
Many thanks!
Dinesh

---

### Post by dinesh2n on 2008-05-27
it is one's luck that if he could get response here. I posted whatever question; I myself posted ans TOO!! ...but alright it might be useful for some others...

ACTUALLY IN IN MY CASE I WAS WORKING ON A SCIENTIFIC CODE. I had nothing to do with the coding of that software. I were just running that code.
THE CAUSE OF "SEGMENTATION ERROR" WAS ONE OF INPUT FILE WAS WRONG....SO I REPLACED THAT BY RIGHT ONE  WHICH LED MY PROGRAMME TO RUN.

---

### Post by sdennie on 2008-05-27
For future reference, when you see a segfault of a custom app, running your application under gdb and typing "where" when it crashes may shed some light on what's going on (it also may not).  In your case, I assume you are using a script so, you'd have to edit the script and proceed the thing that's actually executing with the command "gdb".

---

