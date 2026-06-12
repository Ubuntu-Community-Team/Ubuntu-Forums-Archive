---
title: "Gprolog 1.3.0: relocation R_predicate error"
date: 2016-12-09
forum: General Help
---

### Post by Syzygia on 2016-12-09
Good morning,

I'm using Ubuntu 16.10, and I just installed gprolog 1.3.0 from Synaptic. However, when I try to compile valid prolog files, I get 

*"relocation R_predicate(&#65533;/64)_32S against `.text' can not be used when making a shared object; recompile with -fPIC"*

error messages. I'm not sure what I should recompile with -fPIC flag.

I have googled this error message, but I haven't been able to fix my problem. I would really appreciate if someone could help me.

More information:
**ex.pl:**
```
sudoku(Puzzle, Solution) :-
    Solution = Puzzle,
    Puzzle = [S11, S12, S13, S14,
              S21, S22, S23, S24,
              S31, S32, S33, S34,
              S41, S42, S43, S44],

    Row1 = [S11, S12, S13, S14],
    Row2 = [S21, S22, S23, S24],
    Row3 = [S31, S32, S33, S34],
    Row4 = [S41, S42, S43, S44],

    Col1 = [S11, S21, S31, S41],
    Col2 = [S12, S22, S32, S42],
    Col3 = [S13, S23, S33, S43],
    Col4 = [S14, S24, S34, S44],

    Square1 = [S11, S12, S21, S22],
    Square2 = [S13, S14, S23, S24],
    Square3 = [S31, S32, S41, S42],
    Square4 = [S33, S34, S43, S44],

    Sets = [Row1, Row2, Row3, Row4,
           Col1, Col2, Col3, Col4,
           Square1, Square2, Square3, Square4],

    maplist(permutation([1,2,3,4]), Sets).

```
```

gplc ex.pl

/usr/bin/ld: Warning: alignment 8 of symbol `init_stream_supp' in /usr/lib/gprolog-iso/libbips_pl.a(stream_supp.o) is smaller than 16 in /usr/lib/gprolog-iso/libengine_pl.a(engine.o)
/usr/bin/ld: Warning: alignment 8 of symbol `fd_reset_solver' in /usr/lib/gprolog-iso/libengine_fd.a(fd_inst.o) is smaller than 16 in /usr/lib/gprolog-iso/libengine_pl.a(if_no_fd.o)
/usr/bin/ld: /tmp/gplcKec9Cg.o: relocation R_predicate(&#65533;/64)_32S against `.text' can not be used when making a shared object; recompile with -fPIC
/usr/bin/ld: /usr/lib/gprolog-iso/all_pl_bips.o: relocation R_predicate(&#65533;/64)_32S against `.text' can not be used when making a shared object; recompile with -fPIC
/usr/bin/ld: /usr/lib/gprolog-iso/all_fd_bips.o: relocation R_predicate(&#65533;/64)_32S against `.text' can not be used when making a shared object; recompile with -fPIC
/usr/bin/ld: /usr/lib/gprolog-iso/top_level.o: relocation R_predicate(&#65533;/64)_32S against `.text' can not be used when making a shared object; recompile with -fPIC
/usr/bin/ld: /usr/lib/gprolog-iso/debugger.o: relocation R_predicate(&#65533;/64)_32S against `.text' can not be used when making a shared object; recompile with -fPIC
/usr/bin/ld: /usr/lib/gprolog-iso/libbips_fd.a(fd_infos.o): relocation R_predicate(&#65533;/64)_32S against `.text' can not be used when making a shared object; recompile with -fPIC
/usr/bin/ld: /usr/lib/gprolog-iso/libbips_fd.a(fd_values.o): relocation R_predicate(&#65533;/64)_32S against `.text' can not be used when making a shared object; recompile with -fPIC
/usr/bin/ld: /usr/lib/gprolog-iso/libbips_fd.a(fd_values_c.o): relocation R_predicate(&#65533;/64)_32S against `.rodata' can not be used when making a shared object; recompile with -fPIC
/usr/bin/ld: /usr/lib/gprolog-iso/libbips_fd.a(fd_math.o): relocation R_predicate(&#65533;/64)_32S against `.text' can not be used when making a shared object; recompile with -fPIC
/usr/bin/ld: /usr/lib/gprolog-iso/libbips_fd.a(fd_math_fd.o): relocation R_predicate(&#65533;/64)_32 against `.text' can not be used when making a shared object; recompile with -fPIC
/usr/bin/ld: /usr/lib/gprolog-iso/libbips_fd.a(fd_bool.o): relocation R_predicate(&#65533;/64)_32S against `.text' can not be used when making a shared object; recompile with -fPIC
/usr/bin/ld: /usr/lib/gprolog-iso/libbips_fd.a(fd_bool_c.o): relocation R_predicate(&#65533;/64)_32 against `.rodata.str1.1' can not be used when making a shared object; recompile with -fPIC
/usr/bin/ld: /usr/lib/gprolog-iso/libbips_fd.a(fd_bool_fd.o): relocation R_predicate(&#65533;/64)_32 against `.text' can not be used when making a shared object; recompile with -fPIC
/usr/bin/ld: /usr/lib/gprolog-iso/libbips_fd.a(fd_prime.o): relocation R_predicate(&#65533;/64)_32S against `.text' can not be used when making a shared object; recompile with -fPIC
/usr/bin/ld: /usr/lib/gprolog-iso/libbips_fd.a(fd_symbolic.o): relocation R_predicate(&#65533;/64)_32S against `.text' can not be used when making a shared object; recompile with -fPIC
/usr/bin/ld: /usr/lib/gprolog-iso/libbips_fd.a(fd_symbolic_fd.o): relocation R_predicate(&#65533;/64)_32 against `.text' can not be used when making a shared object; recompile with -fPIC
/usr/bin/ld: /usr/lib/gprolog-iso/libbips_fd.a(fd_optim.o): relocation R_predicate(&#65533;/64)_32S against `.text' can not be used when making a shared object; recompile with -fPIC
/usr/bin/ld: /usr/lib/gprolog-iso/libbips_fd.a(math_supp.o): relocation R_predicate(&#65533;/64)_32S against `.bss' can not be used when making a shared object; recompile with -fPIC
/usr/bin/ld: /usr/lib/gprolog-iso/libbips_fd.a(oper_supp.o): relocation R_predicate(&#65533;/64)_32 against `.bss' can not be used when making a shared object; recompile with -fPIC
/usr/bin/ld: /usr/lib/gprolog-iso/libbips_fd.a(fd_prime_c.o): relocation R_predicate(&#65533;/64)_32 against `.rodata.str1.1' can not be used when making a shared object; recompile with -fPIC
/usr/bin/ld: /usr/lib/gprolog-iso/libengine_fd.a(fd_inst.o): relocation R_predicate(&#65533;/64)_32 against `.rodata.str1.1' can not be used when making a shared object; recompile with -fPIC
/usr/bin/ld: /usr/lib/gprolog-iso/libengine_fd.a(fd_range.o): relocation R_predicate(&#65533;/64)_32S against `.rodata' can not be used when making a shared object; recompile with -fPIC
/usr/bin/ld: /usr/lib/gprolog-iso/libengine_fd.a(fd_unify.o): relocation R_predicate(&#65533;/64)_32 against `.text' can not be used when making a shared object; recompile with -fPIC
/usr/bin/ld: /usr/lib/gprolog-iso/libbips_pl.a(error_supp.o): relocation R_predicate(&#65533;/64)_32 against `.rodata.str1.1' can not be used when making a shared object; recompile with -fPIC
/usr/bin/ld: /usr/lib/gprolog-iso/libbips_pl.a(c_supp.o): relocation R_predicate(&#65533;/64)_32S against undefined symbol `atom_tbl' can not be used when making a shared object; recompile with -fPIC
/usr/bin/ld: /usr/lib/gprolog-iso/libbips_pl.a(stream_supp.o): relocation R_predicate(&#65533;/64)_32S against `.bss' can not be used when making a shared object; recompile with -fPIC
/usr/bin/ld: /usr/lib/gprolog-iso/libbips_pl.a(pl_error.o): relocation R_predicate(&#65533;/64)_32S against `.text' can not be used when making a shared object; recompile with -fPIC
/usr/bin/ld: /usr/lib/gprolog-iso/libbips_pl.a(utils.o): relocation R_predicate(&#65533;/64)_32S against `.text' can not be used when making a shared object; recompile with -fPIC
/usr/bin/ld: /usr/lib/gprolog-iso/libbips_pl.a(unify.o): relocation R_predicate(&#65533;/64)_32S against `.text' can not be used when making a shared object; recompile with -fPIC
/usr/bin/ld: /usr/lib/gprolog-iso/libbips_pl.a(assert.o): relocation R_predicate(&#65533;/64)_32S against `.text' can not be used when making a shared object; recompile with -fPIC
/usr/bin/ld: /usr/lib/gprolog-iso/libbips_pl.a(assert_c.o): relocation R_predicate(&#65533;/64)_32 against `.text' can not be used when making a shared object; recompile with -fPIC
/usr/bin/ld: /usr/lib/gprolog-iso/libbips_pl.a(read.o): relocation R_predicate(&#65533;/64)_32S against `.text' can not be used when making a shared object; recompile with -fPIC
/usr/bin/ld: /usr/lib/gprolog-iso/libbips_pl.a(read_c.o): relocation R_predicate(&#65533;/64)_32S against undefined symbol `parse_dico_var' can not be used when making a shared object; recompile with -fPIC
/usr/bin/ld: /usr/lib/gprolog-iso/libbips_pl.a(write.o): relocation R_predicate(&#65533;/64)_32S against `.text' can not be used when making a shared object; recompile with -fPIC
/usr/bin/ld: /usr/lib/gprolog-iso/libbips_pl.a(print.o): relocation R_predicate(&#65533;/64)_32S against `.text' can not be used when making a shared object; recompile with -fPIC
/usr/bin/ld: /usr/lib/gprolog-iso/libbips_pl.a(const_io.o): relocation R_predicate(&#65533;/64)_32S against `.text' can not be used when making a shared object; recompile with -fPIC
/usr/bin/ld: /usr/lib/gprolog-iso/libbips_pl.a(const_io_c.o): relocation R_predicate(&#65533;/64)_32S against undefined symbol `atom_tbl' can not be used when making a shared object; recompile with -fPIC
/usr/bin/ld: /usr/lib/gprolog-iso/libbips_pl.a(oper.o): relocation R_predicate(&#65533;/64)_32S against `.text' can not be used when making a shared object; recompile with -fPIC
/usr/bin/ld: /usr/lib/gprolog-iso/libbips_pl.a(oper_c.o): relocation R_predicate(&#65533;/64)_32 against `.rodata.str1.1' can not be used when making a shared object; recompile with -fPIC
/usr/bin/ld: /usr/lib/gprolog-iso/libbips_pl.a(pred.o): relocation R_predicate(&#65533;/64)_32S against `.text' can not be used when making a shared object; recompile with -fPIC
/usr/bin/ld: /usr/lib/gprolog-iso/libbips_pl.a(pred_c.o): relocation R_predicate(&#65533;/64)_32S against undefined symbol `atom_tbl' can not be used when making a shared object; recompile with -fPIC
/usr/bin/ld: /usr/lib/gprolog-iso/libbips_pl.a(atom.o): relocation R_predicate(&#65533;/64)_32S against `.text' can not be used when making a shared object; recompile with -fPIC
/usr/bin/ld: /usr/lib/gprolog-iso/libbips_pl.a(atom_c.o): relocation R_predicate(&#65533;/64)_32S against undefined symbol `atom_tbl' can not be used when making a shared object; recompile with -fPIC
/usr/bin/ld: /usr/lib/gprolog-iso/libbips_pl.a(control.o): relocation R_predicate(&#65533;/64)_32S against `.text' can not be used when making a shared object; recompile with -fPIC
/usr/bin/ld: /usr/lib/gprolog-iso/libbips_pl.a(control_c.o): relocation R_predicate(&#65533;/64)_32 against `.rodata.str1.1' can not be used when making a shared object; recompile with -fPIC
/usr/bin/ld: /usr/lib/gprolog-iso/libbips_pl.a(call.o): relocation R_predicate(&#65533;/64)_32S against `.text' can not be used when making a shared object; recompile with -fPIC
/usr/bin/ld: /usr/lib/gprolog-iso/libbips_pl.a(call_args.o): relocation R_predicate(&#65533;/64)_32S against `.text' can not be used when making a shared object; recompile with -fPIC
/usr/bin/ld: /usr/lib/gprolog-iso/libbips_pl.a(call_args_c.o): relocation R_predicate(&#65533;/64)_32S against undefined symbol `atom_tbl' can not be used when making a shared object; recompile with -fPIC
/usr/bin/ld: /usr/lib/gprolog-iso/libbips_pl.a(catch.o): relocation R_predicate(&#65533;/64)_32S against `.text' can not be used when making a shared object; recompile with -fPIC
/usr/bin/ld: /usr/lib/gprolog-iso/libbips_pl.a(throw.o): relocation R_predicate(&#65533;/64)_32S against `.text' can not be used when making a shared object; recompile with -fPIC
/usr/bin/ld: /usr/lib/gprolog-iso/libbips_pl.a(throw_c.o): relocation R_predicate(&#65533;/64)_32 against `.rodata.str1.8' can not be used when making a shared object; recompile with -fPIC
/usr/bin/ld: /usr/lib/gprolog-iso/libbips_pl.a(flag.o): relocation R_predicate(&#65533;/64)_32S against `.text' can not be used when making a shared object; recompile with -fPIC
/usr/bin/ld: /usr/lib/gprolog-iso/libbips_pl.a(flag_c.o): relocation R_predicate(&#65533;/64)_32 against `.rodata.str1.1' can not be used when making a shared object; recompile with -fPIC
/usr/bin/ld: /usr/lib/gprolog-iso/libbips_pl.a(arith_inl.o): relocation R_predicate(&#65533;/64)_32S against `.text' can not be used when making a shared object; recompile with -fPIC
/usr/bin/ld: /usr/lib/gprolog-iso/libbips_pl.a(arith_inl_c.o): relocation R_predicate(&#65533;/64)_32 against `.rodata.str1.1' can not be used when making a shared object; recompile with -fPIC
/usr/bin/ld: /usr/lib/gprolog-iso/libbips_pl.a(type_inl.o): relocation R_predicate(&#65533;/64)_32S against `.text' can not be used when making a shared object; recompile with -fPIC
/usr/bin/ld: /usr/lib/gprolog-iso/libbips_pl.a(term_inl.o): relocation R_predicate(&#65533;/64)_32S against `.text' can not be used when making a shared object; recompile with -fPIC
/usr/bin/ld: /usr/lib/gprolog-iso/libbips_pl.a(term_inl_c.o): relocation R_predicate(&#65533;/64)_32 against `.rodata.str1.1' can not be used when making a shared object; recompile with -fPIC
/usr/bin/ld: /usr/lib/gprolog-iso/libbips_pl.a(g_var_inl.o): relocation R_predicate(&#65533;/64)_32S against `.text' can not be used when making a shared object; recompile with -fPIC
/usr/bin/ld: /usr/lib/gprolog-iso/libbips_pl.a(g_var_inl_c.o): relocation R_predicate(&#65533;/64)_32 against `.rodata.str1.1' can not be used when making a shared object; recompile with -fPIC
/usr/bin/ld: /usr/lib/gprolog-iso/libbips_pl.a(all_solut.o): relocation R_predicate(&#65533;/64)_32S against `.text' can not be used when making a shared object; recompile with -fPIC
/usr/bin/ld: /usr/lib/gprolog-iso/libbips_pl.a(all_solut_c.o): relocation R_predicate(&#65533;/64)_32S against undefined symbol `glob_dico_var' can not be used when making a shared object; recompile with -fPIC
/usr/bin/ld: /usr/lib/gprolog-iso/libbips_pl.a(sort.o): relocation R_predicate(&#65533;/64)_32S against `.text' can not be used when making a shared object; recompile with -fPIC
/usr/bin/ld: /usr/lib/gprolog-iso/libbips_pl.a(sort_c.o): relocation R_predicate(&#65533;/64)_32 against `.text' can not be used when making a shared object; recompile with -fPIC
/usr/bin/ld: /usr/lib/gprolog-iso/libbips_pl.a(list.o): relocation R_predicate(&#65533;/64)_32S against `.text' can not be used when making a shared object; recompile with -fPIC
/usr/bin/ld: /usr/lib/gprolog-iso/libbips_pl.a(stat.o): relocation R_predicate(&#65533;/64)_32S against `.text' can not be used when making a shared object; recompile with -fPIC
/usr/bin/ld: /usr/lib/gprolog-iso/libbips_pl.a(stat_c.o): relocation R_predicate(&#65533;/64)_32 against `.rodata.str1.8' can not be used when making a shared object; recompile with -fPIC
/usr/bin/ld: /usr/lib/gprolog-iso/libbips_pl.a(stream.o): relocation R_predicate(&#65533;/64)_32S against `.text' can not be used when making a shared object; recompile with -fPIC
/usr/bin/ld: /usr/lib/gprolog-iso/libbips_pl.a(stream_c.o): relocation R_predicate(&#65533;/64)_32S against undefined symbol `atom_tbl' can not be used when making a shared object; recompile with -fPIC
/usr/bin/ld: /usr/lib/gprolog-iso/libbips_pl.a(file.o): relocation R_predicate(&#65533;/64)_32S against `.text' can not be used when making a shared object; recompile with -fPIC
/usr/bin/ld: /usr/lib/gprolog-iso/libbips_pl.a(file_c.o): relocation R_predicate(&#65533;/64)_32S against undefined symbol `atom_tbl' can not be used when making a shared object; recompile with -fPIC
/usr/bin/ld: /usr/lib/gprolog-iso/libbips_pl.a(char_io.o): relocation R_predicate(&#65533;/64)_32S against `.text' can not be used when making a shared object; recompile with -fPIC
/usr/bin/ld: /usr/lib/gprolog-iso/libbips_pl.a(dec10io.o): relocation R_predicate(&#65533;/64)_32S against `.text' can not be used when making a shared object; recompile with -fPIC
/usr/bin/ld: /usr/lib/gprolog-iso/libbips_pl.a(format.o): relocation R_predicate(&#65533;/64)_32S against `.text' can not be used when making a shared object; recompile with -fPIC
/usr/bin/ld: /usr/lib/gprolog-iso/libbips_pl.a(format_c.o): relocation R_predicate(&#65533;/64)_32 against `.rodata.str1.1' can not be used when making a shared object; recompile with -fPIC
/usr/bin/ld: /usr/lib/gprolog-iso/libbips_pl.a(os_interf.o): relocation R_predicate(&#65533;/64)_32S against `.text' can not be used when making a shared object; recompile with -fPIC
/usr/bin/ld: /usr/lib/gprolog-iso/libbips_pl.a(os_interf_c.o): relocation R_predicate(&#65533;/64)_32 against `.rodata.str1.1' can not be used when making a shared object; recompile with -fPIC
/usr/bin/ld: /usr/lib/gprolog-iso/libbips_pl.a(expand.o): relocation R_predicate(&#65533;/64)_32S against `.text' can not be used when making a shared object; recompile with -fPIC
/usr/bin/ld: /usr/lib/gprolog-iso/libbips_pl.a(expand_c.o): relocation R_predicate(&#65533;/64)_32 against `.rodata.str1.1' can not be used when making a shared object; recompile with -fPIC
/usr/bin/ld: /usr/lib/gprolog-iso/libbips_pl.a(consult.o): relocation R_predicate(&#65533;/64)_32S against `.text' can not be used when making a shared object; recompile with -fPIC
/usr/bin/ld: /usr/lib/gprolog-iso/libbips_pl.a(consult_c.o): relocation R_predicate(&#65533;/64)_32 against `.rodata.str1.1' can not be used when making a shared object; recompile with -fPIC
/usr/bin/ld: /usr/lib/gprolog-iso/libbips_pl.a(pretty.o): relocation R_predicate(&#65533;/64)_32S against `.text' can not be used when making a shared object; recompile with -fPIC
/usr/bin/ld: /usr/lib/gprolog-iso/libbips_pl.a(pretty_c.o): relocation R_predicate(&#65533;/64)_32S against undefined symbol `glob_dico_var' can not be used when making a shared object; recompile with -fPIC
/usr/bin/ld: /usr/lib/gprolog-iso/libbips_pl.a(random.o): relocation R_predicate(&#65533;/64)_32S against `.text' can not be used when making a shared object; recompile with -fPIC
/usr/bin/ld: /usr/lib/gprolog-iso/libbips_pl.a(top_level_c.o): relocation R_predicate(&#65533;/64)_32 against `.rodata.str1.8' can not be used when making a shared object; recompile with -fPIC
/usr/bin/ld: /usr/lib/gprolog-iso/libbips_pl.a(debugger_c.o): relocation R_predicate(&#65533;/64)_32 against `.rodata.str1.1' can not be used when making a shared object; recompile with -fPIC
/usr/bin/ld: /usr/lib/gprolog-iso/libbips_pl.a(src_rdr.o): relocation R_predicate(&#65533;/64)_32S against `.text' can not be used when making a shared object; recompile with -fPIC
/usr/bin/ld: /usr/lib/gprolog-iso/libbips_pl.a(src_rdr_c.o): relocation R_predicate(&#65533;/64)_32 against `.rodata.str1.1' can not be used when making a shared object; recompile with -fPIC
/usr/bin/ld: /usr/lib/gprolog-iso/libbips_pl.a(sockets.o): relocation R_predicate(&#65533;/64)_32S against `.text' can not be used when making a shared object; recompile with -fPIC
/usr/bin/ld: /usr/lib/gprolog-iso/libbips_pl.a(sockets_c.o): relocation R_predicate(&#65533;/64)_32 against `.rodata.str1.1' can not be used when making a shared object; recompile with -fPIC
/usr/bin/ld: /usr/lib/gprolog-iso/libbips_pl.a(le_interf.o): relocation R_predicate(&#65533;/64)_32S against `.text' can not be used when making a shared object; recompile with -fPIC
/usr/bin/ld: /usr/lib/gprolog-iso/libbips_pl.a(le_interf_c.o): relocation R_predicate(&#65533;/64)_32S against undefined symbol `atom_tbl' can not be used when making a shared object; recompile with -fPIC
/usr/bin/ld: /usr/lib/gprolog-iso/libbips_pl.a(pred_supp.o): relocation R_predicate(&#65533;/64)_32S against undefined symbol `atom_tbl' can not be used when making a shared object; recompile with -fPIC
/usr/bin/ld: /usr/lib/gprolog-iso/libbips_pl.a(term_supp.o): relocation R_predicate(&#65533;/64)_32S against `.rodata' can not be used when making a shared object; recompile with -fPIC
/usr/bin/ld: /usr/lib/gprolog-iso/libbips_pl.a(parse_supp.o): relocation R_predicate(&#65533;/64)_32 against `.rodata.str1.1' can not be used when making a shared object; recompile with -fPIC
/usr/bin/ld: /usr/lib/gprolog-iso/libbips_pl.a(write_supp.o): relocation R_predicate(&#65533;/64)_32 against `.rodata.str1.1' can not be used when making a shared object; recompile with -fPIC
/usr/bin/ld: /usr/lib/gprolog-iso/libbips_pl.a(dynam_supp.o): relocation R_predicate(&#65533;/64)_32S against symbol `predicate($scan_dyn_jump_alt/0)' can not be used when making a shared object; recompile with -fPIC
/usr/bin/ld: /usr/lib/gprolog-iso/libbips_pl.a(bc_supp.o): relocation R_predicate(&#65533;/64)_32 against `.rodata.str1.1' can not be used when making a shared object; recompile with -fPIC
/usr/bin/ld: /usr/lib/gprolog-iso/libbips_pl.a(scan_supp.o): relocation R_predicate(&#65533;/64)_32S against undefined symbol `char_conv' can not be used when making a shared object; recompile with -fPIC
/usr/bin/ld: /usr/lib/gprolog-iso/libengine_pl.a(machine.o): relocation R_predicate(&#65533;/64)_32 against `.rodata.str1.8' can not be used when making a shared object; recompile with -fPIC
/usr/bin/ld: /usr/lib/gprolog-iso/libengine_pl.a(machine1.o): relocation R_predicate(&#65533;/64)_32 against undefined symbol `m_architecture' can not be used when making a shared object; recompile with -fPIC
/usr/bin/ld: /usr/lib/gprolog-iso/libengine_pl.a(misc.o): relocation R_predicate(&#65533;/64)_32 against `.text' can not be used when making a shared object; recompile with -fPIC
/usr/bin/ld: /usr/lib/gprolog-iso/libengine_pl.a(hash.o): relocation R_predicate(&#65533;/64)_32 against `.rodata.str1.1' can not be used when making a shared object; recompile with -fPIC
/usr/bin/ld: /usr/lib/gprolog-iso/libengine_pl.a(obj_chain.o): relocation R_predicate(&#65533;/64)_32 against `.bss' can not be used when making a shared object; recompile with -fPIC
/usr/bin/ld: /usr/lib/gprolog-iso/libengine_pl.a(engine.o): relocation R_predicate(&#65533;/64)_32 against `.rodata.str1.1' can not be used when making a shared object; recompile with -fPIC
/usr/bin/ld: /usr/lib/gprolog-iso/libengine_pl.a(wam_inst.o): relocation R_predicate(&#65533;/64)_32 against `.rodata.str1.1' can not be used when making a shared object; recompile with -fPIC
/usr/bin/ld: /usr/lib/gprolog-iso/libengine_pl.a(atom.o): relocation R_predicate(&#65533;/64)_32S against `.bss' can not be used when making a shared object; recompile with -fPIC
/usr/bin/ld: /usr/lib/gprolog-iso/libengine_pl.a(pred.o): relocation R_predicate(&#65533;/64)_32 against undefined symbol `pred_tbl' can not be used when making a shared object; recompile with -fPIC
/usr/bin/ld: /usr/lib/gprolog-iso/libengine_pl.a(oper.o): relocation R_predicate(&#65533;/64)_32 against `.rodata.str1.1' can not be used when making a shared object; recompile with -fPIC
/usr/bin/ld: /usr/lib/gprolog-iso/libengine_pl.a(if_no_fd.o): relocation R_predicate(&#65533;/64)_32 against `.rodata.str1.8' can not be used when making a shared object; recompile with -fPIC
/usr/bin/ld: /usr/lib/gprolog-iso/libengine_pl.a(main.o): relocation R_predicate(&#65533;/64)_32 against `.rodata.str1.8' can not be used when making a shared object; recompile with -fPIC
/usr/bin/ld: /usr/lib/gprolog-iso/liblinedit.a(linedit.o): relocation R_predicate(&#65533;/64)_32S against `.bss' can not be used when making a shared object; recompile with -fPIC
/usr/bin/ld: /usr/lib/gprolog-iso/liblinedit.a(terminal.o): relocation R_predicate(&#65533;/64)_32 against `.rodata.str1.1' can not be used when making a shared object; recompile with -fPIC
/usr/bin/ld: /usr/lib/gprolog-iso/liblinedit.a(ctrl_c.o): relocation R_predicate(&#65533;/64)_32 against `.rodata.str1.8' can not be used when making a shared object; recompile with -fPIC
/usr/bin/ld: final link failed: Nonrepresentable section on output
collect2: error: ld returned 1 exit status
compilation failed

```

Thank you in advance.

---

