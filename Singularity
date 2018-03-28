Bootstrap: shub
From: ucr-singularity/cuda-9.0-base

%post

    # TensorFlow
    pip install --no-cache-dir tensorflow-gpu==1.5.0
    
    # Deep Mind Sonnet
    pip install --no-cache-dir dm-sonnet-gpu==1.17

    # Theano
    pip install --no-cache-dir Theano==1.0.1

    # Keras
    pip install --no-cache-dir keras==2.1.5

    # Pytorch, per pytorch.org recommendation
    pip install --no-cache-dir https://download.pytorch.org/whl/cu90/torch-0.3.1-cp27-cp27mu-linux_x86_64.whl
    pip install --no-cache-dir torchvision==0.2.0

    # OpenCV - necessary downloads
    cd /usr/local/src
    wget https://github.com/opencv/opencv/archive/3.4.1.tar.gz
    tar xzf 3.4.1.tar.gz
    wget -O contrib-3.4.1.tar.gz https://github.com/opencv/opencv_contrib/archive/3.4.1.tar.gz
    tar xzf contrib-3.4.1.tar.gz
    
    # OpenCV - compilation
    cd opencv-3.4.1
    mkdir build
    cd build
    cmake -D CMAKE_BUILD_TYPE=RELEASE \
        -D CMAKE_INSTALL_PREFIX=/usr/local \
        -D INSTALL_PYTHON_EXAMPLES=ON \
        -D INSTALL_C_EXAMPLES=OFF \
        -D OPENCV_EXTRA_MODULES_PATH=/usr/local/src/opencv_contrib-3.4.1/modules \
        -D PYTHON_EXECUTABLE=~/usr/bin/python \
        -D BUILD_EXAMPLES=ON ..   
    make -j 4
    make install
  
    # OpenCV - Symbolic link for cv2.so
    ln -s /usr/local/lib/python2.7/site-packages/cv2.so /usr/local/lib/python2.7/site-packages/cv2.so

    # Cleanup
    rm -rf /usr/local/src/opencv*

