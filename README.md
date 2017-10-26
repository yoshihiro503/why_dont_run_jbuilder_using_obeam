# why_dont_run_jbuilder_using_obeam

## do not run
```console
$ jbuilder build main.exe
      ocamlc main.{cmi,cmo,cmt}
    ocamlopt main.{cmx,o}
    ocamlopt main.exe
$ _build/default/main.exe
$
```

## do run

modify jbuild:

```diff
--- a/jbuild
+++ b/jbuild
@@ -2,4 +2,4 @@
 
 (executable
  ((name main)
-  (libraries (obeam))))
+  (libraries ())))
```

```console
$ jbuilder build main.exe
    ocamldep main.depends.ocamldep-output
      ocamlc main.{cmi,cmo,cmt}
    ocamlopt main.{cmx,o}
    ocamlopt main.exe
$ _build/default/main.exe 
hello, a using obeam project.
```

## my environment

* opam 1.2.2
* ocaml 4.04.2
* jbuilder 1.0+beta11
* obeam 0.0.2
