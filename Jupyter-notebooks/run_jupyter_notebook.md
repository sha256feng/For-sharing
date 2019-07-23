## How to set up Jupyter Notebook connected with a remote cluster/work station? 

### Overview of Major Steps 
1. Run "Jupyter Notebook" without browser on *remote server*;  
   Specify a port for this activity on *remote server*;  
2. Connect through `ssh` from local port to remote port *at local*;  
3. Open webpage on *local* browser;
4. Input token or password in browser;  

### Set-up details  
1. Log into remote server, and type:  
`jupyter notebook --no-browser --port=9000 &`.  
Though we add a `&` at the end, but the terminal is still noisy with lots of output. Ignore it for now^ ^.  

Output:  
```
(base) zju@zju-ROG-STRIX-Z390-F-GAMING:~/QM-prediction/QM-data/dev$ [I 10:17:43.416 NotebookApp] JupyterLab extension loaded from /home/zju/anaconda3/lib/python3.7/site-packages/jupyterlab
[I 10:17:43.416 NotebookApp] JupyterLab application directory is /home/zju/anaconda3/share/jupyter/lab
[I 10:17:43.416 NotebookApp] 启动notebooks 在本地路径: /home/zju/QM-prediction/QM-data/dev
[I 10:17:43.417 NotebookApp] 本程序运行在: http://localhost:9000/?token=3de9c173abf453b19df72a87edf1c2a73c8d84266362f884
...
```

2. Open another terminal on local computer and type:  
`ssh -N -f -L 8888:localhost:9000 username@server.name`.   
This step is connecting the local port `8888` to remote server port `9999`.  

3. Open a web browser on local computer and type `localhost:8888` and enter.  
It will open a webpage prompting input of token. 

4. We get this token from step 1's output, where it says   
`http://localhost:9000/?token=3de9c173abf453b19df72a87edf1c2a73c8d84266362f884`.   
Copy the string after "token=", then we arrive at the directory on remote server where we set up Jupyter Notebook. 


Boo~ Congrats!
