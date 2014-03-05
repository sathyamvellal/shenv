Shell Environments v1.1
=======================

#### Why do you need this?
 
Let's say you are working on something and you've cd'ed to directories deep in your filesystem, you have set up your own aliases, your own functions and other shell variables which help you in executing what you are working on better. Don't you get irritated if you want to open a terminal and want to cd every time, create these functions/variables/aliases, etc? ShEnv helps you in creating mini environments for each of such project directories!

### Shell Support

1. [Bash](https://github.com/sathyamvellal/shenv/tree/master/bash/)


### Advantages/Features

1. You can create closed environments for different projects/activities that you do.
2. While in an environment, if you just `cd` in your terminal, you won't end up in the home directory but rather in the environment's root directory which you specify. 
3. Create variables, alises and functions for an environment and don't even worry about unsetting/unaliasing them!

### Instructions and Usage

For bash users

1. Copy the envrc file `bash/.bashenvrc` to a location you desire and source it in your `.bashrc`
2. You then need to mark a folder for storing all environment scripts that ShEnv creates for you. This is a folder of your choice. Just set the variable `SHENV_HOME` at line 3 in the envrc file.
3. To create a new environment, use `envcreate <name> <directory>` where **name** is the name of the environment and **directory** is the *absolute* path to the environment's root.
4. To start an environment, use `envstart <name>` where name is the name of the environment
5. Similarly, to end the environment, use `envend <name>`. 
6. You can add all your custom aliases, functions, environment variables in the `envinit` funciton in `<name>.shenv.sh` that is created at your `SHENV_HOME` directory.

#### An example (for bash)

There are three associative arrays that ShEnv uses. `variables`, `aliases` and `functions`.  
You populate these in the `envinit` function (as specified above). Like so -

```bash
variables[FILE]='$ENV_ROOT/file.txt'
aliases[run]='rake generate' && 'rake preview'
functions[mkcd]='mkdir -p $1 && cd $1' # NOTE the single quotes !!
```

Once you start the environment with `envstart`, you can use these like any other shell variable, alias or a function. Like so -

```bash
cat $FILE
run # rake generate && rake preview
mkcd foo # create directory 'foo' and cd to it
```

### Coming Next
 
1. Suport for Z-Shell

### License

The MIT License (MIT)

Copyright (c) 2013, Sathyam M Vellal

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in
all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN
THE SOFTWARE.

[1]: https://github.com/sathyamvellal/shenv/blob/master/bash/.bashenvrc#L23
[2]: https://github.com/sathyamvellal/shenv/blob/master/bash/.bashenvrc#L29
