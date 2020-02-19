      *----------------------------------------------------------------*
       IDENTIFICATION DIVISION.
       PROGRAM-ID. PRINCIPAL.
      *----------------------------------------------------------------*
       ENVIRONMENT DIVISION.
       CONFIGURATION SECTION.
      *----------------------------------------------------------------*
       SPECIAL-NAMES.
           DECIMAL-POINT  IS COMMA.
      *----------------------------------------------------------------*
       DATA DIVISION.
       WORKING-STORAGE SECTION.
      *----------------------------------------------------------------*
       
       01  VARIAVEIS-WORKING.
          	05  W-OPCAO-GERAL          PIC 9(001) VALUE ZEROS.
05  W-MSG-TELA			PIC X(001) VALUE SPACES.
         
      *----------------------------------------------------------------*
       PROCEDURE DIVISION.

       00000-PRINCIPAL SECTION.

           PERFORM 10000-INICIA
           PERFORM 20000-PROCESSA
           PERFORM 90000-FINALIZA
           .
       99999-FIM-PRINCIPAL.            EXIT.
      *----------------------------------------------------------------*
     
 *----------------------------------------------------------------*
       10000-INICIA SECTION.
           
        	INITIALIZE VARIAVEIS-WORKING

		PERFORM 11000-MONTA-TELA
           .
       19999-FIM-INICIA.            EXIT.
      *----------------------------------------------------------------*
     
 *----------------------------------------------------------------*
       11000-MONTA-TELA SECTION.
           
     	DISPLAY ERASE
		DISPLAY "SISTEMA DE CLIENTES X VENDEDORES"		AT 0610
        	DISPLAY "CADASTRO"  						AT 0810         
        	DISPLAY "1 – CADASTRO DE CLIENTE" 			AT 0910          
        	DISPLAY "2 – CADASTRO DE VENDEDOR" 			AT 1010
 	DISPLAY "RELATORIOS" 						AT 1210          
     	DISPLAY "3 – RELATORIO DE CLIENTE" 			AT 1310          
     	DISPLAY "4 – RELATORIO DE VENDEDOR"			AT 1410           
DISPLAY "EXECUTAR" 						AT 1610          
     	DISPLAY " 5 – EXECUTAR DISTRIBUICAO DE CLIENTES" AT 1710
DISPLAY "DIGITE A OPCAO DESEJADA" 			AT 1910
ACCEPT W-OPCAO-GERAL						AT 1925
DISPLAY W-MSG-TELA						AT 2125

DISPLAY W-MSG-TELA
           .
       11999-FIM-MONTA-TELA.            EXIT.
      *----------------------------------------------------------------*

*----------------------------------------------------------------*
       20000-PROCESSA SECTION. 
          
EVALUATE W-OPCAO-GERAL
WHEN 1
	CALL CADASTRO-CLIENTE
WHEN 2
	CALL CADASTRO-VENDEDOR
WHEN 3
	CALL RELATORIO-CLIENTE 
WHEN 4
	CALL RELATORIO-VENDEDOR
WHEN 5
	CALL DISTRIBUICAO-CLIENTE
WHEN OTHER
	MOVE “OPCAO INVALIDA” TO W-MSG-TEÇA
	PERFORM 11000-MONTA-TELA
END-EVALUATE.

29999-FIM-PROCESSA.            EXIT.
*----------------------------------------------------------------*

*----------------------------------------------------------------*
 90000-FINALIZA SECTION.

STOP RUN
.
 99999-FIM-FINALIZa.         EXIT.