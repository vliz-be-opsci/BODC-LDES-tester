# BODC-LDES-tester
This repo will is a subset of vliz-be-opsci kgap that can be used to harvest BODC made ldes feeds and test then for LDES spec compliance and completeness by comparing the ldes feed produced with the SPARQL dump BODC also provides


## dependencies
* This assumes you have docker and docker-compose installed

## usage

* Launch a shell / cli to execute some docker commands
```sh
$ docker compose pull      # get all needed docker-images
$ cp dotenv.example .env   # clone the proposed .env 
$ vi .env                  # ... and possibly edit further

$ docker compose up -d     # launch the stack
$ docker compose logs -f   # keep an eye on what the stack is doing
```

Note: we assume this is executed on `localhost`. 
If however you use some remote `dockerhost` then be sure to replace the hostname references in the URL below...

## evaluation


### docker stack inspection

```sh
$ docker compose ps
```

?? should I not see the child processes for the various ldes feeds?



### docker logs
Inspecting the logs should reveal if there are any execution issues 

Typical examples:

* LDES consumer for feed 'xxx' terminated with code 125
  ??? WHAT DOES THIS MEAN

* LDES consumer for feed 'xxx' terminated with code 0 
  ??? WHAT DOES THIS MEAN

* ??? WHY no error messages for BODC?  What does that mean?? 

 
### graphdb inspection

Direct a browser to the [graphdb-ui](http://localhost:7200/)
You should be able to select the bodc_ldes_test repository and inspect available triples... 


?? no entries though ...


### yasgui usage

One could also use the embeded [yasgui](http://localhost:8080/)  to inspect the triples it should be automatically setup to use the relative available graphdb in the docker stack.



?? same result --> nada ??



### jupyter notebook

Finally an embeded [jupyter platform](http://localhost:8889/) with included `.ipynb`
is available.



??? does not work because git is not available in the jupyter image
```
Collecting git+https://github.com/vliz-be-opsci/py-sema.git (from -r requirements.txt (line 12))
  Cloning https://github.com/vliz-be-opsci/py-sema.git to /tmp/pip-req-build-x_mz1q0i
  ERROR: Error [Errno 2] No such file or directory: 'git' while executing command git version
ERROR: Cannot find command 'git' - do you have 'git' installed and in your PATH?
Note: you may need to restart the kernel to use updated packages.
```
