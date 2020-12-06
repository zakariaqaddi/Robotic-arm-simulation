%%Standar DH parametr matrix
syms th d alpha a 

 A=[cos(th) -cos(alpha)*sin(th) sin(th)*sin(alpha)  a*cos(th)
    sin(th) cos(alpha)*cos(th) -cos(th)*sin(alpha)  a*sin(th)
    0             sin(alpha)     cos(alpha)             d
    0                  0              0                  1   ];

% A=trotz(th)*trans1(0,0,d)*trans1(a,0,0)*trotx(alpha)

 %%Link1
  syms th1 L1
  A1=subs(A,{a,alpha,d,th},{0,pi/2,L1,th1});
  
  %%Link2
  syms th2 L2 
  A2=subs(A,{a,alpha,d,th},{L2,0,0,th2});
  
  %%Link3 
  syms th3 L3
  A3=subs(A,{a,alpha,d,th},{0,pi/2,0,th3});
  
   %%Link4
  syms th4 L4 
  A4=subs(A,{a,alpha,d,th},{0,pi/2,L3,th4});
  
   %%Link5
  syms th5 L5 
  A5=subs(A,{a,alpha,d,th},{0,-pi/2,0,th5});
  
   %%Link6
  syms th6 L6 
  A6=subs(A,{a,alpha,d,th},{0,0,L6,th6});

  %%Total Forward matrix 
  
  At=simplify(A1*A2*A3*A4*A5*A6);
  At2=subs(At,{L1,L2,L3,L6},{10,9,9,6});
  
 %get X,Y,Z at zero angles
     q1=0;  q2=0;  q3=0;  q4=0;  q5=0;  q6=0; 
   At3=subs(At2,{th1,th2,th3,th4,th5,th6},{q1,q2,q3,q4,q5,q6})   ;