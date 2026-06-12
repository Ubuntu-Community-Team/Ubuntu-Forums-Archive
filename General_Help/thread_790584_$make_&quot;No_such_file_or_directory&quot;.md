---
title: "$make &quot;No such file or directory&quot;"
date: 2008-05-11
forum: General Help
---

### Post by dinesh2n on 2008-05-11
Hello Dear Friends!
       Please help in following problem I have waisted tooo much time in this. I am working in a scintific code installed in ubuntu. I succeded to "cmake" it (i.e. compile it). But when I execute the command "make" it is showing following error shown below. I know that the file "IncFluid.h" is missing but I don't know how to remove this error. Actually this file is existing there in the Directory trunk" (which can be seen in the following attachment). What i did is that I copied that file from trunk and paste in "src" but still same error is coming. Moreover all the libereries of the code is installed in the root ubuntu; still the compiler could't see the file "IncFluid.h"!!!?
   Kindly, any body point out the error, I would be thankful to him.
Thanks.
dinesh@localhost:~/data_file_new/demo/SPECTRAL/trunk/src$ make 
[  9%] Building CXX object CMakeFiles/RB.dir/main.o
In file included from /home/dinesh/data_file_new/demo/SPECTRAL/trunk/src/main.cc:17:
/home/dinesh/data_file_new/demo/SPECTRAL/trunk/src/main.h:19:26: error: IncFluid.h: No such file or directory
/home/dinesh/data_file_new/demo/SPECTRAL/trunk/src/main.cc:156:64: warning: no newline at end of file
In file included from /home/dinesh/data_file_new/demo/SPECTRAL/trunk/src/main.cc:17:
/home/dinesh/data_file_new/demo/SPECTRAL/trunk/src/main.h:27: error: variable or field ‘Read_prog_para’ declared void
/home/dinesh/data_file_new/demo/SPECTRAL/trunk/src/main.h:27: error: ‘ifstream’ was not declared in this scope
/home/dinesh/data_file_new/demo/SPECTRAL/trunk/src/main.h:27: error: ‘prog_para_file’ was not declared in this scope
/home/dinesh/data_file_new/demo/SPECTRAL/trunk/src/main.h:27: error: ‘string’ was not declared in this scope
/home/dinesh/data_file_new/demo/SPECTRAL/trunk/src/main.h:27: error: ‘prog_kind’ was not declared in this scope
/home/dinesh/data_file_new/demo/SPECTRAL/trunk/src/main.h:27: error: ‘string’ was not declared in this scope
/home/dinesh/data_file_new/demo/SPECTRAL/trunk/src/main.h:27: error: ‘data_dir_name’ was not declared in this scope
/home/dinesh/data_file_new/demo/SPECTRAL/trunk/src/main.h:27: error: expected primary-expression before ‘int’
/home/dinesh/data_file_new/demo/SPECTRAL/trunk/src/main.h:29: error: variable or field ‘Read_field_para’ declared void
/home/dinesh/data_file_new/demo/SPECTRAL/trunk/src/main.h:29: error: ‘ifstream’ was not declared in this scope
/home/dinesh/data_file_new/demo/SPECTRAL/trunk/src/main.h:29: error: ‘field_para_file’ was not declared in this scope
/home/dinesh/data_file_new/demo/SPECTRAL/trunk/src/main.h:29: error: expected primary-expression before ‘int’
/home/dinesh/data_file_new/demo/SPECTRAL/trunk/src/main.h:29: error: expected primary-expression before ‘int’
/home/dinesh/data_file_new/demo/SPECTRAL/trunk/src/main.h:30: error: expected primary-expression before ‘int’
/home/dinesh/data_file_new/demo/SPECTRAL/trunk/src/main.h:30: error: expected primary-expression before ‘double’
/home/dinesh/data_file_new/demo/SPECTRAL/trunk/src/main.h:31: error: ‘string’ was not declared in this scope
/home/dinesh/data_file_new/demo/SPECTRAL/trunk/src/main.h:31: error: ‘basis_type’ was not declared in this scope
/home/dinesh/data_file_new/demo/SPECTRAL/trunk/src/main.h:31: error: ‘string’ was not declared in this scope
/home/dinesh/data_file_new/demo/SPECTRAL/trunk/src/main.h:31: error: ‘alias_switch’ was not declared in this scope
/home/dinesh/data_file_new/demo/SPECTRAL/trunk/src/main.h:31: error: ‘string’ was not declared in this scope
/home/dinesh/data_file_new/demo/SPECTRAL/trunk/src/main.h:31: error: ‘integ_scheme’ was not declared in this scope
/home/dinesh/data_file_new/demo/SPECTRAL/trunk/src/main.h:32: error: expected primary-expression before ‘int’
/home/dinesh/data_file_new/demo/SPECTRAL/trunk/src/main.h:32: error: expected primary-expression before ‘int’
/home/dinesh/data_file_new/demo/SPECTRAL/trunk/src/main.h:33: error: ‘Array’ was not declared in this scope
/home/dinesh/data_file_new/demo/SPECTRAL/trunk/src/main.h:33: error: ‘DP’ was not declared in this scope
/home/dinesh/data_file_new/demo/SPECTRAL/trunk/src/main.h:33: error: ‘time_para’ was not declared in this scope
/home/dinesh/data_file_new/demo/SPECTRAL/trunk/src/main.h:33: error: ‘Array’ was not declared in this scope
/home/dinesh/data_file_new/demo/SPECTRAL/trunk/src/main.h:33: error: ‘DP’ was not declared in this scope
/home/dinesh/data_file_new/demo/SPECTRAL/trunk/src/main.h:33: error: ‘time_save’ was not declared in this scope
/home/dinesh/data_file_new/demo/SPECTRAL/trunk/src/main.h:34: error: ‘string’ was not declared in this scope
/home/dinesh/data_file_new/demo/SPECTRAL/trunk/src/main.h:34: error: ‘nos_output_field_mode’ was not declared in this scope
/home/dinesh/data_file_new/demo/SPECTRAL/trunk/src/main.h:34: error: expected primary-expression before ‘int’
/home/dinesh/data_file_new/demo/SPECTRAL/trunk/src/main.h:35: error: ‘Array’ was not declared in this scope
/home/dinesh/data_file_new/demo/SPECTRAL/trunk/src/main.h:35: error: expected primary-expression before ‘int’
/home/dinesh/data_file_new/demo/SPECTRAL/trunk/src/main.h:35: error: ‘out_k_array’ was not declared in this scope
/home/dinesh/data_file_new/demo/SPECTRAL/trunk/src/main.h:35: error: expected primary-expression before ‘int’
/home/dinesh/data_file_new/demo/SPECTRAL/trunk/src/main.h:36: error: expected primary-expression before ‘int’
/home/dinesh/data_file_new/demo/SPECTRAL/trunk/src/main.h:36: error: expected primary-expression before ‘int’
/home/dinesh/data_file_new/demo/SPECTRAL/trunk/src/main.h:36: error: expected primary-expression before ‘int’
/home/dinesh/data_file_new/demo/SPECTRAL/trunk/src/main.h:37: error: expected primary-expression before ‘int’
/home/dinesh/data_file_new/demo/SPECTRAL/trunk/src/main.h:37: error: ‘Array’ was not declared in this scope
/home/dinesh/data_file_new/demo/SPECTRAL/trunk/src/main.h:37: error: ‘DP’ was not declared in this scope
/home/dinesh/data_file_new/demo/SPECTRAL/trunk/src/main.h:37: error: ‘Rshell’ was not declared in this scope
/home/dinesh/data_file_new/demo/SPECTRAL/trunk/src/main.h:39: error: variable or field ‘Read_init_cond_para’ declared void
/home/dinesh/data_file_new/demo/SPECTRAL/trunk/src/main.h:39: error: ‘ifstream’ was not declared in this scope
/home/dinesh/data_file_new/demo/SPECTRAL/trunk/src/main.h:39: error: ‘init_cond_para_file’ was not declared in this scope
/home/dinesh/data_file_new/demo/SPECTRAL/trunk/src/main.h:39: error: expected primary-expression before ‘int’
/home/dinesh/data_file_new/demo/SPECTRAL/trunk/src/main.h:39: error: expected primary-expression before ‘int’
/home/dinesh/data_file_new/demo/SPECTRAL/trunk/src/main.h:39: error: expected primary-expression before ‘int’
/home/dinesh/data_file_new/demo/SPECTRAL/trunk/src/main.h:40: error: expected primary-expression before ‘int’
/home/dinesh/data_file_new/demo/SPECTRAL/trunk/src/main.h:40: error: ‘Array’ was not declared in this scope
/home/dinesh/data_file_new/demo/SPECTRAL/trunk/src/main.h:40: error: ‘DP’ was not declared in this scope
/home/dinesh/data_file_new/demo/SPECTRAL/trunk/src/main.h:40: error: ‘init_cond_para’ was not declared in this scope
/home/dinesh/data_file_new/demo/SPECTRAL/trunk/src/main.h:41: error: ‘string’ was not declared in this scope
/home/dinesh/data_file_new/demo/SPECTRAL/trunk/src/main.h:41: error: ‘nos_input_field_mode’ was not declared in this scope
/home/dinesh/data_file_new/demo/SPECTRAL/trunk/src/main.h:43: error: variable or field ‘Read_force_para’ declared void
/home/dinesh/data_file_new/demo/SPECTRAL/trunk/src/main.h:43: error: ‘ifstream’ was not declared in this scope
/home/dinesh/data_file_new/demo/SPECTRAL/trunk/src/main.h:43: error: ‘force_field_para_file’ was not declared in this scope
/home/dinesh/data_file_new/demo/SPECTRAL/trunk/src/main.h:43: error: expected primary-expression before ‘int’
/home/dinesh/data_file_new/demo/SPECTRAL/trunk/src/main.h:44: error: expected primary-expression before ‘int’
/home/dinesh/data_file_new/demo/SPECTRAL/trunk/src/main.h:44: error: ‘Array’ was not declared in this scope
/home/dinesh/data_file_new/demo/SPECTRAL/trunk/src/main.h:44: error: ‘DP’ was not declared in this scope
/home/dinesh/data_file_new/demo/SPECTRAL/trunk/src/main.h:44: error: ‘force_field_para’ was not declared in this scope
/home/dinesh/data_file_new/demo/SPECTRAL/trunk/src/main.h:46: error: ‘string’ was not declared in this scope
/home/dinesh/data_file_new/demo/SPECTRAL/trunk/src/main.h:46: error: expected primary-expression before ‘int’
/home/dinesh/data_file_new/demo/SPECTRAL/trunk/src/main.h:46: error: initializer expression list treated as compound expression
/home/dinesh/data_file_new/demo/SPECTRAL/trunk/src/main.h:47: error: ‘string’ was not declared in this scope
/home/dinesh/data_file_new/demo/SPECTRAL/trunk/src/main.h:47: error: expected primary-expression before ‘int’
/home/dinesh/data_file_new/demo/SPECTRAL/trunk/src/main.h:47: error: initializer expression list treated as compound expression
/home/dinesh/data_file_new/demo/SPECTRAL/trunk/src/main.h:48: error: ‘string’ was not declared in this scope
/home/dinesh/data_file_new/demo/SPECTRAL/trunk/src/main.h:48: error: expected primary-expression before ‘int’
/home/dinesh/data_file_new/demo/SPECTRAL/trunk/src/main.h:48: error: initializer expression list treated as compound expression
/home/dinesh/data_file_new/demo/SPECTRAL/trunk/src/main.h:49: error: ‘string’ was not declared in this scope
/home/dinesh/data_file_new/demo/SPECTRAL/trunk/src/main.h:49: error: expected primary-expression before ‘int’
/home/dinesh/data_file_new/demo/SPECTRAL/trunk/src/main.h:49: error: initializer expression list treated as compound expression
/home/dinesh/data_file_new/demo/SPECTRAL/trunk/src/main.h:50: error: ‘string’ was not declared in this scope
/home/dinesh/data_file_new/demo/SPECTRAL/trunk/src/main.h:50: error: expected primary-expression before ‘int’
/home/dinesh/data_file_new/demo/SPECTRAL/trunk/src/main.h:50: error: initializer expression list treated as compound expression
/home/dinesh/data_file_new/demo/SPECTRAL/trunk/src/main.cc:21: error: ‘fftw_plan’ does not name a type
/home/dinesh/data_file_new/demo/SPECTRAL/trunk/src/main.cc:22: error: ‘fftw_plan’ does not name a type
/home/dinesh/data_file_new/demo/SPECTRAL/trunk/src/main.cc:25: error: expected constructor, destructor, or type conversion before ‘<’ token
/home/dinesh/data_file_new/demo/SPECTRAL/trunk/src/main.cc: In function ‘int main(int, char**)’:
/home/dinesh/data_file_new/demo/SPECTRAL/trunk/src/main.cc:36: error: ‘string’ was not declared in this scope
/home/dinesh/data_file_new/demo/SPECTRAL/trunk/src/main.cc:36: error: expected `;' before ‘prog_kind’
/home/dinesh/data_file_new/demo/SPECTRAL/trunk/src/main.cc:37: error: expected `;' before ‘data_dir_name’
/home/dinesh/data_file_new/demo/SPECTRAL/trunk/src/main.cc:40: error: ‘cout’ was not declared in this scope
/home/dinesh/data_file_new/demo/SPECTRAL/trunk/src/main.cc:40: error: ‘prog_kind’ was not declared in this scope
/home/dinesh/data_file_new/demo/SPECTRAL/trunk/src/main.cc:40: error: ‘endl’ was not declared in this scope
/home/dinesh/data_file_new/demo/SPECTRAL/trunk/src/main.cc:41: error: ‘data_dir_name’ was not declared in this scope
/home/dinesh/data_file_new/demo/SPECTRAL/trunk/src/main.cc:67: error: ‘SPECrand’ was not declared in this scope
/home/dinesh/data_file_new/demo/SPECTRAL/trunk/src/main.cc:79: error: ‘Ifluid_main’ cannot be used as a function
/home/dinesh/data_file_new/demo/SPECTRAL/trunk/src/main.cc:82: error: ‘Ipassive_scalar_main’ cannot be used as a function
/home/dinesh/data_file_new/demo/SPECTRAL/trunk/src/main.cc:85: error: ‘IMHD_main’ cannot be used as a function
/home/dinesh/data_file_new/demo/SPECTRAL/trunk/src/main.cc:88: error: ‘RB_slip_main’ cannot be used as a function
/home/dinesh/data_file_new/demo/SPECTRAL/trunk/src/main.cc:91: error: ‘RB_slipMHD_main’ cannot be used as a function
/home/dinesh/data_file_new/demo/SPECTRAL/trunk/src/main.cc: At global scope:
/home/dinesh/data_file_new/demo/SPECTRAL/trunk/src/main.cc:107: error: variable or field ‘Read_prog_para’ declared void
/home/dinesh/data_file_new/demo/SPECTRAL/trunk/src/main.cc:107: error: ‘ifstream’ was not declared in this scope
/home/dinesh/data_file_new/demo/SPECTRAL/trunk/src/main.cc:107: error: ‘prog_para_file’ was not declared in this scope
/home/dinesh/data_file_new/demo/SPECTRAL/trunk/src/main.cc:107: error: ‘string’ was not declared in this scope
/home/dinesh/data_file_new/demo/SPECTRAL/trunk/src/main.cc:107: error: ‘prog_kind’ was not declared in this scope
/home/dinesh/data_file_new/demo/SPECTRAL/trunk/src/main.cc:107: error: ‘string’ was not declared in this scope
/home/dinesh/data_file_new/demo/SPECTRAL/trunk/src/main.cc:107: error: ‘data_dir_name’ was not declared in this scope
/home/dinesh/data_file_new/demo/SPECTRAL/trunk/src/main.cc:107: error: expected primary-expression before ‘int’
make[2]: *** [CMakeFiles/RB.dir/main.o] Error 1
make[1]: *** [CMakeFiles/RB.dir/all] Error 2
make: *** [all] Error 2

---

### Post by dinesh2n on 2008-05-12
hi 
I just have got the ans of question by myself.....actually i had to erase the cmakecache.txt and then had to apply the command "cmake" and "make"in "trunk". which solved my problem.....
thanks !

---

