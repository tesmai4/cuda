# Compile the my CUDA examples

CC=g++
CUDACC=nvcc

CFLAGS=-ggdb
CUDACFLAGS=-m64

LDFLAGS=-L/usr/local/cuda/lib -lcuda -lcublas -lcudart 
RM=rm -rf

CUDA_SOURCES=imgproc.cu
SOURCES=imgproc_main.cpp
CUDA_OBJECTS=$(CUDA_SOURCES:.cu=.o)
OBJECTS=$(SOURCES:.cpp=.o)

.SUFFIXES: .cpp .cu .o

all: imgproc

imgproc: imgproc.h $(OBJECTS) $(CUDA_OBJECTS)
	$(CC) -lopencv_core -lopencv_highgui -lopencv_imgproc $(LDFLAGS) $(CUDA_OBJECTS) $(OBJECTS) -o imgproc

clean:
	$(RM) *.o imgproc

.cpp.o:
	$(CC) $(CFLAGS) $< -c -o $@

.cu.o:
	$(CUDACC) $(CUDACFLAGS) $< -c -o $@
