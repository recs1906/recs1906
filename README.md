disp('PRACTICA #3');
disp('HERNANDEZ AGUILLON ADOLFO');
opc1= input ('Tipo de onductor (1)ACSR (2)Sólido');
disp ('');
if opc1 == 1
    disp ('ACSR');
    opc2 = input ('Línea (1)Monofásica (2)Trifasica'); 
    disp ('');
   
    if opc2 == 1
        disp ('Línea monofásica, conductor individual');
            D1=input ('Ingrese la distancia entre conductores monofasico ===');
            disp ('');
            GMR=input ('Ingrese GMR del conductor (metros)===');
            disp ('');
            log1= input('Ingrese la longuitud (Km)===');
            disp (''); 
            L=0.2*log(D1/GMR)
            Lt= L*log1
    end
if opc2 == 2
        disp ('Línea trifásica');
        opc3=input('Es (1)Circuito simple (2)Circuito doble');  
        disp('');
            disp('help');
            GMR1= input('Valor del GMR extraído de la tabla (metros)');  
disp ('');
NC=input('Ingrese el numero de conductores  ');  
disp (' ');
entradas=1;
for i=1:NC
   entradas(i)=input(['Ingrese la distancia del conductor ' num2str(i) '=']); 
end
RC=1;
for i=1:NC
    RC=RC*entradas(i);
end
GMRL=(RC)^(1/3)
if opc3==1
L=0.2*log(GMRL/GMR1)
    else opc3==2
    d=input ('distancia entre subconductores = ');
    disp(' ');
    SCL=input('Ingrese el numero de subconductores inductancia 3 4 5 = ');
         disp (' ');
         if SCL==3
          AA=sqrt(GMR1*d);
    disp(['el haz de subconductores en inductancia es: ' num2str(AA)]);
    if SCL==4
        AA=sqrt(GMR1*(d^2));
        disp(['el haz de subconductores en inductancia es: ' num2str(AA)]);
    else 
        if SCL==5
            AA=(1.094)*sqrt(GMR1*(d^3))
            disp(['el haz de subconductores en inductancia es: ' num2str(AA)]);
        else 
        end
    end
         end
      L=0.2*log(GMRL/AA)
end
        disp ('nice')
end
 
 else  opc1==2
    disp ('Sólido');
     opc4 = input ('Línea (1)Monofásica (2)Trifasica'); 
    disp ('');
    if opc4 == 1
        disp ('Sólido monofásico');
Rx=input('Ingrese el radio "x" (metros)=');
disp (' ');
Ry=input('Ingrese el radio "y" (metros)=');
disp (' ')
Log2=input('Distancia de la línea de transmisión (km)=');
disp (' ')

Subconductoresx=input  ('Ingrese conductores de ida x=');
Subconductoresy=input  ('Ingrese conductores de ida y=');
nx=Subconductoresx^2-Subconductoresx;
ny=Subconductoresy^2-Subconductoresy;
 entradas=1;  %crea una matriz
for i = 1:nx
   entradas(i)=input(['Ingrese la distancia x ' num2str(i) '=']); 
end
     Mx=1;  
    for i = 1:nx
    Mx = Mx * entradas(i); 
    end
 entradas=1; 
for i = 1:ny
   entradas(i)=input(['Ingrese la distancia y ' num2str(i) '=']); 
end
     My=1;  
    for i = 1:ny
    My = My * entradas(i); 
    end
   
   
NM=Subconductoresx*Subconductoresy;
entradas=1;
for i = 1:NM
    entradas(i)=input(['Ingrese la distancia entre subconductores de las fases( ' num2str(i) ')= ']);
end
Ra=1;
for i=1:NM
    Ra= Ra * entradas (i);
end
GMD1=(Ra)^(1/NM);
Dsx=(Rx)*(2.71828^(-1/4));
Dsy=(Ry)*(2.71828^(-1/4));
GMRx=((Dsx^Subconductoresx)*(Mx))^(1/Subconductoresx^2);
GMRy=((Dsy^Subconductoresy)*(My))^(1/Subconductoresy^2);
Lx=0.2*log(GMD1/GMRx)
Ly=0.2*log(GMD1/GMRy)
L=(Lx*Log2)+(Ly*Log2)
XLT=(2*pi*60*L)   
        end

    if opc4 == 2
        disp ('Sólido trifasico');
        
        Ds=input ('Añada el Ds=GMR=r de la tabla segun sea dicho el conductor= ');
disp(' ');
d=input ('distancia entre subconductores= ');
disp(' ');
SubconductoresA=input('Número de subconductores de (A)=');
SubconductoresB=input('Número de subconductores de (B)=');
SubconductoresC=input('Número de subconductores de (C)=');
nA=SubconductoresA*SubconductoresB;
nB=SubconductoresB*SubconductoresC;
nC=SubconductoresA*SubconductoresC;
entradas=1;  
for i = 1:nA
   entradas(i)=input(['Ingrese la distancia Da-b ' num2str(i) '=']);
end
     rA=1;  
    for i = 1:nA
    rA = rA * entradas(i); 
    end
 entradas=1;
for i = 1:nB
   entradas(i)=input(['Ingrese la distancia Db-c ' num2str(i) '=']); 
end
     rB=1;  
    for i = 1:nB
    rB = rB * entradas(i); 
    end
 entradas=1;
 for i = 1:nC
   entradas(i)=input(['Ingrese la distancia Da-c ' num2str(i) '=']); 
end
     rC=1;  
    for i = 1:nC
    rC = rC * entradas(i); 
    end
Dab=(rA)^(1/4);
Dbc=(rB)^(1/4);
Dac=(rC)^(1/4);
GMD=(Dab*Dbc*Dac)^(1/3);

Nh=input('Número de haz por sub-conductor 1)2 haz por sub-conductores 2)3 haz por sub-conductores 3)4 haz por sub-conductores=');
disp ('');
if Nh==1
    Dsb=sqrt(Ds*d);
    disp(['el haz de subconductores es: ' num2str(Dsb)]);
else 
    if Nh==2
        Dsb=sqrt(Ds*(d^2));
        disp(['el haz de subconductores es: ' num2str(Dsb)]);
    else 
        if Nh==3
            Dsb=(1.094)*sqrt(Ds*(d^3))
            disp(['el haz de subconductores es: ' num2str(Dsb)]);
        else 
            disp ('Error')
        end
    end
end
Daa=input ('distancia entre subconductores Da-ap= ');
disp(' ');
Dbb=input ('distancia entre subconductores Db-bp= ');
disp(' ');
Dcc=input ('distancia entre subconductores Dc-cp= ');
disp(' ');
Dsa=sqrt(Dsb*Daa);
DsB=sqrt(Dsb*Dbb);
Dsc=sqrt(Dsb*Dcc);
GMR=(Dsa*DsB*Dsc)^(1/3)
L=0.2*log((GMD)/(GMR))
    end
    end
